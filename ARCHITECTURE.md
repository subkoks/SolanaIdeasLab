# Architecture Documentation

> System design patterns, database schemas, and integration contracts for SolanaIdeasLab projects.

---

## System Architecture Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend Apps  │    │   API Gateway    │    │  Backend Services│
│                 │    │                 │    │                 │
│ • Next.js Apps   │◄──►│ • Auth Middleware│◄──►│ • FastAPI/Node  │
│ • React Components│    │ • Rate Limiting  │    │ • Business Logic │
│ • TailwindCSS    │    │ • Load Balancing │    │ • Data Processing│
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Shared UI      │    │   Shared Auth    │    │   Shared DB      │
│                 │    │                 │    │                 │
│ • Components     │    │ • JWT Sessions   │    │ • PostgreSQL     │
│ • Design System  │    │ • Wallet Connect │    │ • Supabase       │
│ • Patterns       │    │ • Subscription   │    │ • Migrations     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ External APIs    │    │   Monitoring     │    │   Infrastructure │
│                 │    │                 │    │                 │
│ • Solana RPC     │    │ • Prometheus     │    │ • Docker         │
│ • Helius API     │    │ • Grafana        │    │ • CI/CD          │
│ • Jupiter API    │    │ • Structured Log │    │ • Vercel/Railway │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

---

## Database Architecture

### Core Schema Design

```sql
-- Users and Authentication
users (id, wallet_address, email, subscription_tier, metadata)
subscriptions (id, user_id, tier, status, stripe_subscription_id)
api_keys (id, user_id, name, key_hash, permissions, expires_at)

-- Project-Specific Tables (examples)
token_alerts (id, user_id, token_address, alert_type, criteria, active)
wallet_tracked (id, user_id, wallet_address, tracking_config)
safety_scans (id, token_address, risk_score, scan_results, timestamp)

-- Audit and Analytics
audit_logs (id, user_id, action, resource_type, metadata, created_at)
usage_metrics (id, user_id, project, action_count, timestamp)
```

### Data Flow Patterns

1. **User Registration**: Wallet connect → JWT token → User record → Subscription tier
2. **API Requests**: JWT validation → Rate limiting → Business logic → Database
3. **Real-time Updates**: WebSocket → Redis cache → Client push notifications
4. **Background Jobs**: Queue system → Worker processes → Database updates

---

## API Design Patterns

### RESTful API Structure

```
/api/v1/
├── auth/
│   ├── POST /wallet/connect
│   ├── POST /wallet/disconnect
│   ├── GET  /profile
│   └── POST /refresh
├── users/
│   ├── GET  /me
│   ├── PUT  /me
│   └── GET  /me/subscription
├── projects/
│   ├── token-sniper/
│   │   ├── GET  /alerts
│   │   ├── POST /alerts
│   │   └── DELETE /alerts/:id
│   ├── wallet-tracker/
│   │   ├── GET  /tracked
│   │   ├── POST /tracked
│   │   └── GET  /tracked/:address/activity
│   └── safety-suite/
│       ├── POST /scan
│       ├── GET  /scan/:token
│       └── GET  /scan/history
└── admin/
    ├── GET  /metrics
    ├── GET  /users
    └── POST /announcements
```

### WebSocket Events

```typescript
// Real-time events for different projects
interface WebSocketEvents {
  // Token Sniper Bot
  'token:launch': { token: string; risk: number; social: SocialData }
  'token:volume_spike': { token: string; volume: number; price: number }
  
  // Wallet Tracker
  'wallet:transaction': { wallet: string; tx: Transaction }
  'wallet:balance_change': { wallet: string; balance: number; token: string }
  
  // Safety Suite
  'safety:risk_alert': { token: string; risk: number; reason: string }
  'safety:bundle_detected': { token: string; wallets: string[] }
}
```

---

## Microservice Architecture

### Service Decomposition

1. **Authentication Service** (`auth-service`)
   - Wallet connection handling
   - JWT token management
   - Subscription validation

2. **Data Service** (`data-service`)
   - Solana RPC interactions
   - External API integrations
   - Data processing and caching

3. **Notification Service** (`notification-service`)
   - Telegram bot integration
   - Email notifications
   - WebSocket push notifications

4. **Analytics Service** (`analytics-service`)
   - Usage metrics collection
   - Performance monitoring
   - Business intelligence

5. **Project Services** (one per major project)
   - `token-sniper-service`
   - `wallet-tracker-service`
   - `safety-suite-service`

### Inter-Service Communication

```typescript
// Service mesh using Redis pub/sub
interface ServiceMessage {
  type: string
  service: string
  data: any
  timestamp: number
  correlationId?: string
}

// Example: Token launch detected
{
  type: 'token_launch_detected',
  service: 'data-service',
  data: {
    tokenAddress: '...',
    metadata: { name: '...', symbol: '...' }
  },
  timestamp: 1672531200000,
  correlationId: 'uuid-here'
}
```

---

## Security Architecture

### Multi-Layer Security

1. **Network Layer**
   - API Gateway with rate limiting
   - DDoS protection
   - SSL/TLS encryption

2. **Application Layer**
   - JWT token validation
   - Role-based access control
   - Input validation and sanitization

3. **Data Layer**
   - Row Level Security (RLS)
   - Encrypted sensitive data
   - Regular security audits

4. **Infrastructure Layer**
   - Container security scanning
   - Secret management
   - Access logging and monitoring

### Security Patterns

```typescript
// Authentication middleware example
export const authMiddleware = async (req: Request, res: Response, next: NextFunction) => {
  const token = req.headers.authorization?.replace('Bearer ', '')
  
  if (!token) {
    return res.status(401).json({ error: 'No token provided' })
  }
  
  try {
    const user = await verifyJWT(token)
    req.user = user
    
    // Check subscription tier for premium features
    if (requiresPremium(req.path) && user.subscriptionTier === 'free') {
      return res.status(403).json({ error: 'Premium subscription required' })
    }
    
    next()
  } catch (error) {
    res.status(401).json({ error: 'Invalid token' })
  }
}
```

---

## Performance Architecture

### Caching Strategy

```typescript
// Multi-level caching
interface CacheStrategy {
  // L1: In-memory cache (Redis)
  redis: {
    userSessions: 'session:{userId}'
    apiResponses: 'api:{endpoint}:{params}'
    realTimeData: 'live:{token}'
  }
  
  // L2: Database cache (PostgreSQL)
  database: {
    materializedViews: ['token_metrics', 'user_stats']
    indexedQueries: ['wallet_transactions', 'token_alerts']
  }
  
  // L3: CDN cache (Vercel/Cloudflare)
  cdn: {
    staticAssets: '/*.{js,css,images}'
    apiResponses: '/api/v1/projects/*/public/*'
  }
}
```

### Scalability Patterns

1. **Horizontal Scaling**: Load balancer → Multiple API instances
2. **Database Scaling**: Read replicas + Connection pooling
3. **Queue Processing**: Redis → Multiple worker processes
4. **CDN Distribution**: Global edge caching

---

## Deployment Architecture

### Container Strategy

```dockerfile
# Multi-stage builds for optimization
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

FROM node:18-alpine AS runtime
WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY . .
EXPOSE 8000
CMD ["npm", "start"]
```

### Environment Configuration

```yaml
# docker-compose.prod.yml
version: '3.8'
services:
  api:
    image: solana-ideas-lab/api:latest
    environment:
      - NODE_ENV=production
      - DATABASE_URL=${DATABASE_URL}
      - REDIS_URL=${REDIS_URL}
    deploy:
      replicas: 3
      resources:
        limits:
          cpus: '0.5'
          memory: 512M
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

---

## Monitoring Architecture

### Observability Stack

1. **Metrics Collection**: Prometheus + custom exporters
2. **Logging**: Structured JSON logs + ELK stack
3. **Tracing**: OpenTelemetry + Jaeger
4. **Alerting**: Grafana + AlertManager

### Key Metrics

```typescript
// Business metrics
interface BusinessMetrics {
  userAcquisition: number
  subscriptionRevenue: number
  apiUsage: { endpoint: string; calls: number }[]
  projectMetrics: {
    tokenSniper: { alertsCreated: number; activeAlerts: number }
    walletTracker: { walletsTracked: number; transactions: number }
    safetySuite: { scansPerformed: number; risksDetected: number }
  }
}

// Technical metrics
interface TechnicalMetrics {
  responseTime: { p50: number; p95: number; p99: number }
  errorRate: number
  throughput: number
  resourceUtilization: {
    cpu: number
    memory: number
    disk: number
  }
}
```

---

## Integration Patterns

### External API Integrations

```typescript
// Solana RPC integration
class SolanaClient {
  private connection: Connection
  private rpcPool: Connection[]
  
  async getTokenMetadata(address: string): Promise<TokenMetadata> {
    // Load balance across RPC endpoints
    const connection = this.getRandomConnection()
    return connection.getParsedAccountInfo(new PublicKey(address))
  }
  
  async subscribeToAccount(address: string, callback: (data: any) => void) {
    // WebSocket subscription with reconnection logic
    const connection = this.getOptimalConnection()
    return connection.onAccountChange(new PublicKey(address), callback)
  }
}

// Helius API integration
class HeliusClient {
  async getWebhookEvents(webhookId: string): Promise<WebhookEvent[]> {
    return this.request(`/webhooks/${webhookId}/events`)
  }
  
  async createWebhook(config: WebhookConfig): Promise<Webhook> {
    return this.request('/webhooks', 'POST', config)
  }
}
```

---

## Development Architecture

### Local Development Setup

```bash
# Development environment
docker-compose -f docker-compose.dev.yml up -d

# Services included:
# - PostgreSQL (port 5432)
# - Redis (port 6379)
# - Local Solana validator (port 8899)
# - Mock external APIs
```

### Code Organization

```
projects/
├── shared/
│   ├── auth/           # Authentication patterns
│   ├── database/       # Database schemas and migrations
│   ├── api/           # API middleware and patterns
│   ├── ui/            # Reusable components
│   ├── monitoring/    # Logging and metrics
│   └── deployment/    # Docker and CI/CD configs
├── token-sniper-bot/
│   ├── src/
│   │   ├── services/   # Business logic
│   │   ├── handlers/   # API endpoints
│   │   ├── models/     # Data models
│   │   └── utils/      # Helper functions
│   ├── tests/
│   ├── docs/
│   └── deploy/
└── [other projects...]
```

---

## Migration Strategy

### Database Migrations

```typescript
// Version-controlled migrations
interface Migration {
  version: string
  description: string
  up: () => Promise<void>
  down: () => Promise<void>
}

// Example migration
const migration001: Migration = {
  version: '001',
  description: 'Create users table',
  up: async () => {
    await sql`
      CREATE TABLE users (
        id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
        wallet_address VARCHAR(44) UNIQUE NOT NULL,
        created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
      )
    `
  },
  down: async () => {
    await sql`DROP TABLE users`
  }
}
```

### Zero-Downtime Deployments

1. **Blue-Green Deployment**: Switch traffic between identical environments
2. **Canary Releases**: Gradually roll out to subset of users
3. **Feature Flags**: Toggle functionality without deployment
4. **Database Backups**: Automated backups before migrations

---

This architecture provides a solid foundation for building scalable, maintainable Solana applications with proper separation of concerns, security, and observability.
