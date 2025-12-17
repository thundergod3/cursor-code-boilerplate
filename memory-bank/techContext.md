# Technical Context

**Last Updated:** {{DATE}}  
**Tech Stack Version:** {{VERSION}}

---

## Technology Stack

### Core Technologies

| Layer | Technology | Version | Purpose |
|-------|------------|---------|---------|
| Language | {{LANGUAGE}} | [Version] | Primary programming language |
| Runtime | [Runtime] | [Version] | Execution environment |
| Package Manager | {{PACKAGE_MANAGER}} | [Version] | Dependency management |
| Backend Framework | {{BACKEND_FRAMEWORK}} | [Version] | API/server framework |
| Frontend Framework | {{FRONTEND_FRAMEWORK}} | [Version] | UI framework |
| Database | [Database] | [Version] | Data persistence |
| ORM | {{DATABASE_ORM}} | [Version] | Database interface |
| Testing | {{TESTING_FRAMEWORK}} | [Version] | Test framework |
| Linter/Formatter | {{LINTER_FORMATTER}} | [Version] | Code quality |

---

## Development Environment Setup

### Prerequisites

1. **[Runtime]** - Version [X.X.X] or higher
2. **[Package Manager]** - Version [X.X.X] or higher
3. **[Database]** - Version [X.X.X] or higher
4. **Git** - Version control

### Installation Steps

```bash
# 1. Clone repository
git clone [repository-url]
cd [project-name]

# 2. Install dependencies
{{PACKAGE_MANAGER}} install

# 3. Setup environment variables
cp .env.example .env
# Edit .env with your local configuration

# 4. Setup database
{{PACKAGE_MANAGER}} run db:setup

# 5. Run migrations
{{PACKAGE_MANAGER}} run db:migrate

# 6. Seed database (optional)
{{PACKAGE_MANAGER}} run db:seed

# 7. Start development server
{{PACKAGE_MANAGER}} run dev
```

### Environment Variables

**Required:**
```bash
DATABASE_URL=          # Database connection string
API_KEY=              # API key for [service]
JWT_SECRET=           # Secret for JWT signing
```

**Optional:**
```bash
PORT=                 # Server port (default: 3000)
NODE_ENV=             # Environment (development/production)
LOG_LEVEL=            # Logging level (debug/info/warn/error)
```

---

## Project Scripts

### Development

```bash
# Start development server with hot reload
{{PACKAGE_MANAGER}} run dev

# Run development server in debug mode
{{PACKAGE_MANAGER}} run dev:debug

# Watch mode for backend only
{{PACKAGE_MANAGER}} run dev:backend

# Watch mode for frontend only
{{PACKAGE_MANAGER}} run dev:frontend
```

### Testing

```bash
# Run all tests
{{PACKAGE_MANAGER}} test

# Run tests in watch mode
{{PACKAGE_MANAGER}} run test:watch

# Run tests with coverage
{{PACKAGE_MANAGER}} run test:coverage

# Run specific test file
{{PACKAGE_MANAGER}} test [path-to-test]

# Run e2e tests
{{PACKAGE_MANAGER}} run test:e2e
```

### Quality Checks

```bash
# Type checking
{{PACKAGE_MANAGER}} run typecheck

# Linting
{{PACKAGE_MANAGER}} run lint

# Fix lint issues automatically
{{PACKAGE_MANAGER}} run lint:fix

# Format code
{{PACKAGE_MANAGER}} run format

# All quality checks at once
{{PACKAGE_MANAGER}} run quality
```

### Database

```bash
# Run migrations
{{PACKAGE_MANAGER}} run db:migrate

# Rollback last migration
{{PACKAGE_MANAGER}} run db:rollback

# Reset database
{{PACKAGE_MANAGER}} run db:reset

# Seed database
{{PACKAGE_MANAGER}} run db:seed

# Generate migration
{{PACKAGE_MANAGER}} run db:migration:create [name]

# Studio/GUI (if supported)
{{PACKAGE_MANAGER}} run db:studio
```

### Build & Deploy

```bash
# Build for production
{{PACKAGE_MANAGER}} run build

# Preview production build
{{PACKAGE_MANAGER}} run preview

# Start production server
{{PACKAGE_MANAGER}} start

# Build and analyze bundle
{{PACKAGE_MANAGER}} run build:analyze
```

---

## Dependencies

### Core Dependencies

```json
{
  "dependencies": {
    "{{BACKEND_FRAMEWORK}}": "^[version]",
    "{{FRONTEND_FRAMEWORK}}": "^[version]",
    "{{DATABASE_ORM}}": "^[version]",
    "[other-core-dep-1]": "^[version]",
    "[other-core-dep-2]": "^[version]"
  }
}
```

### Development Dependencies

```json
{
  "devDependencies": {
    "{{TESTING_FRAMEWORK}}": "^[version]",
    "{{LINTER_FORMATTER}}": "^[version]",
    "@types/[types]": "^[version]",
    "[other-dev-dep-1]": "^[version]",
    "[other-dev-dep-2]": "^[version]"
  }
}
```

### Why We Chose These

| Dependency | Rationale |
|------------|-----------|
| {{BACKEND_FRAMEWORK}} | [Why we chose this framework] |
| {{FRONTEND_FRAMEWORK}} | [Why we chose this framework] |
| {{DATABASE_ORM}} | [Why we chose this ORM] |
| {{TESTING_FRAMEWORK}} | [Why we chose this test framework] |

---

## Configuration Files

### TypeScript Configuration

**File:** `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "noEmitOnError": true
  }
}
```

### Linter Configuration

**File:** [linter config file]

```json
[Configuration details]
```

### Test Configuration

**File:** [test config file]

```json
[Configuration details]
```

---

## Database Schema

### Tables

#### Table 1: [table_name]
```sql
CREATE TABLE [table_name] (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  [column1] VARCHAR(255) NOT NULL,
  [column2] TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**Indexes:**
- `idx_[table]_[column]` on `[column]`

**Relationships:**
- Belongs to: [other_table]
- Has many: [other_table]

#### Table 2: [table_name]
```sql
CREATE TABLE [table_name] (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  [column1] VARCHAR(255) NOT NULL,
  [foreign_key_id] UUID REFERENCES [other_table](id),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**Indexes:**
- `idx_[table]_[column]` on `[column]`

**Relationships:**
- Belongs to: [other_table]

---

## API Documentation

### Base URL
- **Development**: `http://localhost:[PORT]`
- **Staging**: `https://staging.[domain].com`
- **Production**: `https://api.[domain].com`

### Authentication

**Method:** [JWT/API Key/OAuth]

**Header:**
```
Authorization: Bearer [token]
```

### Endpoints

#### GET /api/[resource]
**Description:** Get all [resources]

**Query Parameters:**
- `page` (number): Page number (default: 1)
- `limit` (number): Items per page (default: 10)
- `sort` (string): Sort field
- `order` (string): Sort order (asc/desc)

**Response:**
```json
{
  "data": [],
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 100
  }
}
```

#### GET /api/[resource]/:id
**Description:** Get single [resource] by ID

**Response:**
```json
{
  "data": {
    "id": "uuid",
    "field1": "value",
    "field2": "value"
  }
}
```

#### POST /api/[resource]
**Description:** Create new [resource]

**Request Body:**
```json
{
  "field1": "value",
  "field2": "value"
}
```

**Response:**
```json
{
  "data": {
    "id": "uuid",
    "field1": "value",
    "field2": "value"
  }
}
```

#### PUT /api/[resource]/:id
**Description:** Update [resource]

**Request Body:**
```json
{
  "field1": "new value",
  "field2": "new value"
}
```

#### DELETE /api/[resource]/:id
**Description:** Delete [resource]

**Response:**
```json
{
  "message": "Resource deleted successfully"
}
```

---

## External Integrations

### Integration 1: [Service Name]

**Purpose:** [What this integration does]

**Configuration:**
```bash
SERVICE_API_KEY=[key]
SERVICE_BASE_URL=[url]
```

**Usage:**
```{{LANGUAGE}}
[Code example]
```

**Rate Limits:**
- Requests per minute: [number]
- Requests per day: [number]

### Integration 2: [Service Name]

**Purpose:** [What this integration does]

**Configuration:**
```bash
SERVICE_API_KEY=[key]
SERVICE_BASE_URL=[url]
```

**Usage:**
```{{LANGUAGE}}
[Code example]
```

---

## Infrastructure

### Development

- **Database**: Local [database type]
- **Caching**: [Redis/Memcached] (local)
- **File Storage**: Local filesystem
- **Email**: [MailHog/Mailtrap]

### Staging

- **Hosting**: [AWS/GCP/Azure/Vercel/etc.]
- **Database**: [Managed database service]
- **Caching**: [Redis Cloud/etc.]
- **File Storage**: [S3/GCS/etc.]
- **CDN**: [CloudFront/Cloudflare/etc.]

### Production

- **Hosting**: [AWS/GCP/Azure/Vercel/etc.]
- **Database**: [Managed database service]
- **Caching**: [Redis Cloud/etc.]
- **File Storage**: [S3/GCS/etc.]
- **CDN**: [CloudFront/Cloudflare/etc.]
- **Monitoring**: [DataDog/NewRelic/etc.]
- **Error Tracking**: [Sentry/Rollbar/etc.]

---

## Performance Targets

| Metric | Target | Current |
|--------|--------|---------|
| API Response Time (p95) | < 200ms | [X]ms |
| Page Load Time (p95) | < 2s | [X]s |
| Time to Interactive | < 3s | [X]s |
| Database Query Time (p95) | < 50ms | [X]ms |
| Uptime | > 99.9% | [X]% |

---

## Troubleshooting

### Common Issues

#### Issue 1: [Problem]
**Symptom:** [What you see]

**Cause:** [Why it happens]

**Solution:**
```bash
[Steps to fix]
```

#### Issue 2: [Problem]
**Symptom:** [What you see]

**Cause:** [Why it happens]

**Solution:**
```bash
[Steps to fix]
```

---

## Useful Commands

### Docker (if using)

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f [service]

# Rebuild containers
docker-compose up -d --build
```

### Database Management

```bash
# Connect to database
[database-cli command]

# Backup database
[backup command]

# Restore database
[restore command]
```

---

**Note:** Update this file when technical stack changes or new tools/services are added.


