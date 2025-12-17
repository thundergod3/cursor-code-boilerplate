# System Patterns

**Last Updated:** {{DATE}}  
**Architecture Version:** {{VERSION}}

---

## System Architecture

### Architecture Style
[Monolith / Microservices / Serverless / Hybrid]

**Rationale:** [Why we chose this approach]

### High-Level Architecture

```
┌─────────────────────────────────────────────┐
│                Frontend                      │
│  [Framework: {{FRONTEND_FRAMEWORK}}]        │
└─────────────┬───────────────────────────────┘
              │
              │ HTTP/WebSocket
              │
┌─────────────▼───────────────────────────────┐
│              API Gateway                     │
│  [Framework: {{BACKEND_FRAMEWORK}}]         │
└─────────────┬───────────────────────────────┘
              │
         ┌────┴────┬────────┐
         │         │        │
    ┌────▼───┐ ┌──▼───┐ ┌─▼────┐
    │Service │ │Service│ │Service│
    │   1    │ │   2   │ │   3  │
    └────┬───┘ └──┬───┘ └─┬────┘
         │        │       │
         └────┬───┴───┬───┘
              │       │
         ┌────▼───────▼──────┐
         │    Database       │
         │ [{{DATABASE_ORM}}]│
         └───────────────────┘
```

---

## Core Design Patterns

### Pattern 1: [Pattern Name]
**Usage:** [Where/when we use this]

**Example:**
```{{LANGUAGE}}
[Code example showing the pattern]
```

**Benefits:**
- [Benefit 1]
- [Benefit 2]

### Pattern 2: [Pattern Name]
**Usage:** [Where/when we use this]

**Example:**
```{{LANGUAGE}}
[Code example showing the pattern]
```

**Benefits:**
- [Benefit 1]
- [Benefit 2]

### Pattern 3: [Pattern Name]
**Usage:** [Where/when we use this]

**Example:**
```{{LANGUAGE}}
[Code example showing the pattern]
```

**Benefits:**
- [Benefit 1]
- [Benefit 2]

---

## Project Structure

### Directory Layout

```
project-root/
├── src/
│   ├── api/              # API routes/endpoints
│   ├── services/         # Business logic
│   ├── models/           # Data models
│   ├── utils/            # Utility functions
│   ├── middleware/       # Middleware
│   ├── validators/       # Input validation schemas
│   └── types/            # Type definitions
├── tests/
│   ├── unit/             # Unit tests
│   ├── integration/      # Integration tests
│   └── e2e/              # End-to-end tests
├── docs/                 # Additional documentation
├── scripts/              # Build/deployment scripts
├── memory-bank/          # Project memory bank
├── .cursorrules          # Cursor AI rules
└── [config files]
```

### File Organization Principles
1. **Colocation**: Keep related files together
2. **Separation of Concerns**: Each directory has a single purpose
3. **Discoverability**: Clear naming and structure
4. **Scalability**: Easy to add new features

---

## Data Flow

### Request Flow
```
1. User Action (Frontend)
   ↓
2. API Request
   ↓
3. Route Handler
   ↓
4. Validation (Middleware)
   ↓
5. Service Layer (Business Logic)
   ↓
6. Data Layer (Database)
   ↓
7. Response Processing
   ↓
8. API Response
   ↓
9. Frontend Update
```

### Data Flow Diagram

```
┌─────────┐      ┌──────────┐      ┌─────────┐
│ Client  │─────▶│   API    │─────▶│ Service │
│         │      │  Layer   │      │  Layer  │
└─────────┘      └──────────┘      └────┬────┘
     ▲                                   │
     │                                   ▼
     │           ┌──────────┐      ┌─────────┐
     └───────────│ Response │◀─────│   DB    │
                 │ Format   │      │  Layer  │
                 └──────────┘      └─────────┘
```

---

## Component Relationships

### Backend Components

#### API Layer
- **Responsibility**: Handle HTTP requests/responses
- **Dependencies**: Service layer, validators
- **Patterns**: RESTful routing, middleware chain

#### Service Layer
- **Responsibility**: Business logic and orchestration
- **Dependencies**: Data layer, external APIs
- **Patterns**: Service locator, dependency injection

#### Data Layer
- **Responsibility**: Database operations
- **Dependencies**: ORM, database
- **Patterns**: Repository pattern, query builders

### Frontend Components

#### Pages/Views
- **Responsibility**: Route-level components
- **Dependencies**: Components, hooks, state management
- **Patterns**: Container/presentational

#### Components
- **Responsibility**: Reusable UI elements
- **Dependencies**: UI library, utilities
- **Patterns**: Atomic design, composition

#### State Management
- **Responsibility**: Application state
- **Dependencies**: State library
- **Patterns**: [Zustand/Jotai/Redux/etc.]

---

## Key Technical Decisions

### Decision 1: [Decision Name]
**Date:** [Date]

**Context:**
[What situation led to this decision]

**Decision:**
[What we decided to do]

**Rationale:**
[Why we chose this approach]

**Consequences:**
- Positive: [Benefits]
- Negative: [Trade-offs]
- Risks: [Potential issues]

**Alternatives Considered:**
1. [Alternative 1]: [Why not chosen]
2. [Alternative 2]: [Why not chosen]

### Decision 2: [Decision Name]
**Date:** [Date]

**Context:**
[What situation led to this decision]

**Decision:**
[What we decided to do]

**Rationale:**
[Why we chose this approach]

**Consequences:**
- Positive: [Benefits]
- Negative: [Trade-offs]
- Risks: [Potential issues]

**Alternatives Considered:**
1. [Alternative 1]: [Why not chosen]
2. [Alternative 2]: [Why not chosen]

---

## Integration Patterns

### External APIs
| Service | Purpose | Pattern | Auth Method |
|---------|---------|---------|-------------|
| [API 1] | [Purpose] | [REST/GraphQL/etc.] | [API Key/OAuth/etc.] |
| [API 2] | [Purpose] | [REST/GraphQL/etc.] | [API Key/OAuth/etc.] |

### Event Handling
- **Pattern**: [Event-driven/Message queue/etc.]
- **Implementation**: [Tools/libraries used]
- **Use Cases**: [When we use this]

### Caching Strategy
- **Level 1**: [Browser/CDN caching]
- **Level 2**: [Application caching]
- **Level 3**: [Database caching]

---

## Error Handling Strategy

### Error Types
1. **Validation Errors**: User input issues
   - Status: 400
   - Format: `{ error: string, field?: string }`

2. **Authentication Errors**: Auth failures
   - Status: 401
   - Format: `{ error: string }`

3. **Authorization Errors**: Permission issues
   - Status: 403
   - Format: `{ error: string }`

4. **Not Found Errors**: Resource not found
   - Status: 404
   - Format: `{ error: string }`

5. **Server Errors**: Internal failures
   - Status: 500
   - Format: `{ error: string }`

### Error Handling Pattern
```{{LANGUAGE}}
[Example of how we handle errors consistently]
```

---

## Security Patterns

### Authentication
- **Method**: [JWT/Session/OAuth/etc.]
- **Storage**: [Where tokens are stored]
- **Expiration**: [Token lifetime]
- **Refresh**: [How tokens are refreshed]

### Authorization
- **Model**: [RBAC/ABAC/etc.]
- **Implementation**: [How we check permissions]
- **Enforcement**: [Where checks happen]

### Data Protection
- **At Rest**: [Encryption method]
- **In Transit**: [TLS/HTTPS]
- **Sensitive Data**: [Special handling]

---

## Testing Strategy

### Unit Tests
- **Coverage Target**: 80%+
- **Framework**: {{TESTING_FRAMEWORK}}
- **Pattern**: AAA (Arrange, Act, Assert)
- **Mocking**: [Mocking strategy]

### Integration Tests
- **Scope**: API endpoints, database operations
- **Framework**: {{TESTING_FRAMEWORK}}
- **Database**: [Test database strategy]

### E2E Tests
- **Scope**: Critical user flows
- **Framework**: [Playwright/Cypress/etc.]
- **Environment**: [Staging/dedicated test env]

---

## Performance Considerations

### Backend
- **Database**: Indexed queries, connection pooling
- **Caching**: [Redis/Memcached strategy]
- **Rate Limiting**: [Implementation]
- **Async Operations**: [Queue/background jobs]

### Frontend
- **Code Splitting**: Route-based splitting
- **Lazy Loading**: Images, components
- **Memoization**: Expensive calculations
- **State Updates**: Optimized re-renders

---

## Deployment Pattern

### Environments
1. **Development**: Local development
2. **Staging**: Pre-production testing
3. **Production**: Live environment

### CI/CD Pipeline
```
Code Push → Tests → Build → Deploy to Staging → Manual Approval → Deploy to Production
```

### Deployment Strategy
- **Method**: [Blue-green/Rolling/Canary]
- **Rollback**: [Rollback procedure]
- **Monitoring**: [Health checks, alerts]

---

**Note:** Update this file when making architectural changes or discovering new patterns.


