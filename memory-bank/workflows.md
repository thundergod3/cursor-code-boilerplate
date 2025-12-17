# Development Workflows

**Last Updated:** {{DATE}}

---

## Overview

This document describes the workflows and approaches for different types of development tasks. While Cursor AI is a unified assistant, these workflows help guide the approach based on the type of work being done.

---

## Workflow 1: Full-Stack Feature Implementation

### When to Use
- Building new features that span backend and frontend
- Creating complete user flows
- Implementing API endpoints with UI

### Prerequisites: Load Project Context

Before ANY implementation:

1. **Read** `.cursorrules` for project coding standards
2. **Read** `memory-bank/techContext.md` for tech stack reference
3. **Read** `memory-bank/systemPatterns.md` for architecture patterns
4. **Read** `memory-bank/activeContext.md` for current work
5. **Check** existing code patterns in the project

### Implementation Steps

#### 1. Understand Requirements
- Read the task/issue carefully
- Identify frontend vs backend vs fullstack requirements
- Check for data model requirements
- Determine which packages/modules to use
- Ask clarifying questions if needed

#### 2. Check Project Context
```bash
# Check project structure
ls -la
cat package.json  # or pyproject.toml, go.mod, Cargo.toml

# Check existing patterns
ls src/
ls src/routes/ src/api/ src/services/

# Check dependencies
cat package.json | grep dependencies
```

#### 3. Follow Project Patterns
- Match existing code style
- Use project's preferred libraries
- Follow established directory structure
- Use project's validation approach

#### 4. Implement with Best Practices

**Backend Checklist:**
- [ ] Input validation on all endpoints
- [ ] Proper error handling
- [ ] Logging for debugging
- [ ] Database transactions where needed
- [ ] Proper HTTP status codes

**Frontend Checklist:**
- [ ] Loading states
- [ ] Error handling and display
- [ ] Form validation
- [ ] Responsive design
- [ ] Accessibility basics

**Full-Stack Checklist:**
- [ ] Type safety end-to-end
- [ ] API error handling
- [ ] Optimistic updates where appropriate
- [ ] Cache invalidation

#### 5. Test Implementation
```bash
# Type check
{{PACKAGE_MANAGER}} run typecheck

# Lint
{{PACKAGE_MANAGER}} run lint

# Test
{{PACKAGE_MANAGER}} run test

# Build
{{PACKAGE_MANAGER}} run build
```

#### 6. Update Documentation
- Update `memory-bank/activeContext.md` with changes
- Update `memory-bank/progress.md` with completion status
- Update `.cursorrules` if new patterns discovered

---

## Workflow 2: Code Review & Investigation

### When to Use
- Reviewing code quality and architecture
- Investigating bugs or performance issues
- Analyzing technical debt
- Root cause analysis

### Investigation Process

#### 1. Gather Information

**Questions to Answer:**
- What is the exact issue or unexpected behavior?
- When did it start occurring?
- Is it reproducible? Steps to reproduce?
- What is expected vs actual behavior?
- Any error messages or stack traces?
- Which environment(s) affected?

**Commands to Run:**
```bash
# Check recent changes
git log --oneline --since="3 days ago" --all

# Search for error messages in code
grep -r "error message" src/

# Check for related commits
git log --all --grep="related keyword"
```

#### 2. Reproduce the Issue

```bash
# Run related tests
{{PACKAGE_MANAGER}} test -- "related-pattern"

# Run application locally
{{PACKAGE_MANAGER}} run dev

# Document exact reproduction steps
```

#### 3. Analyze Root Cause

**For Backend Issues:**
```bash
# Check API endpoint logic
grep -r "endpoint-path" src/

# Check database queries
grep -r "SELECT\|INSERT\|UPDATE" src/

# Check middleware/interceptors
grep -r "middleware\|interceptor" src/
```

**For Frontend Issues:**
```bash
# Check component logic
grep -r "ComponentName" src/

# Check state management
grep -r "useState\|useStore\|atom" src/

# Check API calls
grep -r "fetch\|axios\|api\." src/
```

#### 4. Common Bug Patterns

**Race Conditions:**
```typescript
// ❌ BAD: Doesn't wait for promise
async function bad() {
  let data;
  fetchData().then(result => data = result);
  return data; // undefined!
}

// ✅ GOOD
async function good() {
  const data = await fetchData();
  return data;
}
```

**Missing Error Handling:**
```typescript
// ❌ BAD
const response = await fetch('/api/data');
return response.json(); // Can throw!

// ✅ GOOD
const response = await fetch('/api/data');
if (!response.ok) {
  throw new Error(`API error: ${response.status}`);
}
return response.json();
```

**Memory Leaks (React):**
```typescript
// ❌ BAD: Missing cleanup
useEffect(() => {
  const interval = setInterval(fetchData, 1000);
  // Missing cleanup!
}, []);

// ✅ GOOD
useEffect(() => {
  const interval = setInterval(fetchData, 1000);
  return () => clearInterval(interval);
}, []);
```

**N+1 Queries:**
```typescript
// ❌ BAD: N+1 query
for (const user of users) {
  const posts = await db.query.posts.findMany({
    where: eq(posts.userId, user.id)
  });
}

// ✅ GOOD: Single query with join
const usersWithPosts = await db.query.users.findMany({
  with: { posts: true }
});
```

#### 5. Code Review Checklist

**Universal Checklist:**
- [ ] Code follows project conventions (check `.cursorrules`)
- [ ] No hardcoded secrets or credentials
- [ ] Input validation present
- [ ] Error handling implemented
- [ ] No obvious security vulnerabilities
- [ ] Tests cover new functionality
- [ ] No debugging code left (console.log, print, etc.)

**Language-Specific:**

**TypeScript/JavaScript:**
- [ ] No `any` types
- [ ] Proper async/await usage
- [ ] No unused imports/variables
- [ ] Proper null/undefined handling

**Python:**
- [ ] Type hints present
- [ ] No bare except clauses
- [ ] Context managers used for resources
- [ ] PEP 8 compliant

**Go:**
- [ ] Errors handled (not ignored)
- [ ] Context used appropriately
- [ ] No goroutine leaks
- [ ] Proper defer usage

**Rust:**
- [ ] No unwrap() in production code
- [ ] Proper Result/Option handling
- [ ] No unsafe blocks (unless justified)
- [ ] Clippy warnings addressed

---

## Workflow 3: Test Creation & QA

### When to Use
- Writing unit tests, integration tests, e2e tests
- Test plan creation
- Test coverage analysis
- Quality assurance

### Testing Process

#### 1. Analyze Requirements
- Understand what needs to be tested
- Identify critical paths and edge cases
- Check existing test coverage

#### 2. Check Current Coverage
```bash
# JavaScript/TypeScript
{{PACKAGE_MANAGER}} test --coverage

# Python
pytest --cov=src --cov-report=html

# Go
go test -cover ./...

# Rust
cargo tarpaulin
```

#### 3. Write Tests Following AAA Pattern

**Arrange** → Set up test data and conditions  
**Act** → Execute the code being tested  
**Assert** → Verify the expected outcome

#### 4. Test Examples by Language

**TypeScript (Vitest):**
```typescript
import { describe, it, expect, beforeEach, vi } from 'vitest';

describe('UserService', () => {
  let service: UserService;
  let mockDb: MockDb;

  beforeEach(() => {
    // Arrange: Setup
    mockDb = createMockDb();
    service = new UserService(mockDb);
  });

  describe('createUser', () => {
    it('should create user with valid data', async () => {
      // Arrange
      const userData = { email: 'test@test.com', name: 'Test' };
      
      // Act
      const user = await service.createUser(userData);
      
      // Assert
      expect(user).toBeDefined();
      expect(user.email).toBe(userData.email);
    });

    it('should throw error for invalid email', async () => {
      // Arrange
      const userData = { email: 'invalid', name: 'Test' };
      
      // Act & Assert
      await expect(service.createUser(userData))
        .rejects.toThrow('Invalid email');
    });
  });
});
```

**Python (pytest):**
```python
import pytest
from unittest.mock import Mock

class TestUserService:
    @pytest.fixture
    def service(self, mock_db):
        return UserService(mock_db)
    
    def test_create_user_valid_data(self, service):
        # Arrange
        user_data = {"email": "test@test.com", "name": "Test"}
        
        # Act
        user = service.create_user(user_data)
        
        # Assert
        assert user is not None
        assert user["email"] == user_data["email"]
    
    def test_create_user_invalid_email(self, service):
        # Arrange
        user_data = {"email": "invalid", "name": "Test"}
        
        # Act & Assert
        with pytest.raises(ValueError, match="Invalid email"):
            service.create_user(user_data)
```

#### 5. Edge Cases to Test

**Input Validation:**
- [ ] Empty strings
- [ ] Null/undefined values
- [ ] Extremely long strings
- [ ] Special characters
- [ ] SQL injection attempts
- [ ] XSS attempts

**Numeric Values:**
- [ ] Zero
- [ ] Negative numbers
- [ ] Very large numbers
- [ ] Floating point precision

**Collections:**
- [ ] Empty arrays/lists
- [ ] Single item
- [ ] Large collections

**Async Operations:**
- [ ] Timeout scenarios
- [ ] Network failures
- [ ] Race conditions

**Error Scenarios:**
- [ ] Database connection failures
- [ ] API failures
- [ ] Permission denied

#### 6. Quality Standards

| Metric | Minimum | Target |
|--------|---------|--------|
| Statements | 80% | 90% |
| Branches | 75% | 85% |
| Functions | 80% | 90% |
| Lines | 80% | 90% |

---

## Workflow 4: UI/UX Review

### When to Use
- Reviewing application design
- Ensuring consistent user experience
- Validating accessibility
- Providing design recommendations

### Review Process

#### 1. Analyze Current UI
- Review the implementation
- Check against design principles
- Test accessibility

#### 2. Consistency Checks

**Visual Design:**
- [ ] **Consistency**: Unified design language
- [ ] **Hierarchy**: Clear visual importance
- [ ] **Typography**: Readable fonts (16px minimum body text)
- [ ] **Color**: Accessible contrast ratios (4.5:1 for text)
- [ ] **Spacing**: Consistent padding/margins (4px or 8px grid)
- [ ] **Alignment**: Proper grid usage

**User Experience:**
- [ ] **Clarity**: Users understand what to do next
- [ ] **Feedback**: Visual feedback for interactions
- [ ] **Error Handling**: Clear, helpful error messages
- [ ] **Load Times**: Skeleton screens, progress indicators
- [ ] **Navigation**: Intuitive menu structure
- [ ] **Forms**: Clear labels, inline validation

#### 3. Accessibility (WCAG 2.1 AA)
- [ ] Keyboard navigation support
- [ ] Screen reader compatibility
- [ ] Color contrast compliance
- [ ] Text resizing support (up to 200%)
- [ ] Alternative text for images
- [ ] Form labels properly associated

#### 4. Responsive Design
- [ ] Mobile-first approach
- [ ] Touch-friendly targets (minimum 44x44px)
- [ ] Readable text without zooming
- [ ] No horizontal scrolling
- [ ] Optimized images for various resolutions

---

## Workflow 5: Architecture Design

### When to Use
- Designing system architecture
- Creating technical specifications
- Defining data models
- Making technology stack decisions

### Design Process

#### 1. Review Requirements
- Analyze business requirements
- Understand constraints
- Identify scalability needs

#### 2. Design Components

**System Architecture:**
- Component diagram
- Data flow diagram
- Integration patterns
- Security boundaries

**Database Design:**
- ER diagrams
- Schema definitions
- Indexing strategy
- Migration plan

**API Design:**
- Endpoint structure
- Request/response formats
- Authentication/authorization
- Rate limiting

#### 3. Document Decisions

For each significant decision, create an ADR:

**Context:** What forces are at play?  
**Decision:** What we decided to do  
**Rationale:** Why we chose this approach  
**Consequences:** Trade-offs and risks  
**Alternatives:** What else was considered

#### 4. Design Principles
- Follow SOLID principles
- Design for failure
- Separation of concerns
- Loose coupling, high cohesion
- API-first design
- Security by design

---

## Workflow 6: Requirements Analysis

### When to Use
- Analyzing business requirements
- Creating user stories
- Defining acceptance criteria
- Translating business needs to technical specs

### Analysis Process

#### 1. Gather Requirements
- Document all stated requirements
- Ask clarifying questions
- Identify ambiguities or conflicts

#### 2. Create User Stories

**Format:**
As a [user type]  
I want to [action]  
So that [benefit]

**Acceptance Criteria:**
- Given [context]
- When [action]
- Then [expected outcome]

#### 3. Prioritize (MoSCoW)
- **Must Have**: Critical features
- **Should Have**: Important but not critical
- **Could Have**: Nice to have
- **Won't Have**: Out of scope

#### 4. Define Success Metrics
- How we measure achievement
- Key performance indicators
- User satisfaction metrics

---

## Quality Gates: NEVER Skip

Before ANY commit, ensure:

1. **Type checking** passes
2. **Linting** passes
3. **Tests** pass
4. **Build** succeeds

```bash
{{PACKAGE_MANAGER}} run typecheck
{{PACKAGE_MANAGER}} run lint
{{PACKAGE_MANAGER}} run test
{{PACKAGE_MANAGER}} run build
```

**No exceptions. No bypassing with `--no-verify`.**

---

## After Every Significant Change

1. Update `memory-bank/activeContext.md` with changes
2. Update `memory-bank/progress.md` with status
3. Update other memory-bank files as needed
4. Update `.cursorrules` if new patterns discovered
5. Run quality gates

---

**Note:** These workflows guide the approach to different types of work. Adapt based on project needs while maintaining quality standards.


