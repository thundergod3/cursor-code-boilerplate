# Cursor Commands for Agent-Based Workflows

This directory contains custom Cursor commands that replicate the specialized agent workflows from Claude Code.

## Available Commands

### `/implement` - Full-Stack Developer Mode
**Use when:** Building features that span both frontend and backend

**What it does:**
- Loads project context from `.cursorrules` and `memory-bank/`
- Implements full-stack features following project patterns
- Ensures type safety, validation, error handling
- Runs quality gates (typecheck, lint, test, build)
- Updates documentation after changes

**Example usage:**
```
/implement Create a user authentication system with JWT tokens and login UI
```

---

### `/frontend` - Frontend Developer Mode
**Use when:** Building UI components, pages, state management, user interactions

**What it does:**
- Focuses on UI/UX implementation with React/Vue/Svelte
- Implements responsive design and accessibility (WCAG)
- Handles state management (React Query, Zustand, forms)
- Optimizes performance (code splitting, memoization, virtual scrolling)
- Ensures proper loading/error states
- Tests component behavior and accessibility

**Example usage:**
```
/frontend Create a responsive user profile component with form validation
```

---

### `/backend` - Backend Developer Mode
**Use when:** Building APIs, database schemas, authentication, background jobs

**What it does:**
- Focuses on API development with proper validation
- Implements authentication/authorization (JWT, RBAC)
- Designs database schemas and migrations
- Optimizes queries and prevents N+1 problems
- Implements caching strategies
- Ensures security best practices
- Tests business logic and integrations

**Example usage:**
```
/backend Create a REST API for blog posts with pagination and role-based access
```

---

### `/review` - Principal Engineer Mode
**Use when:** Reviewing code, investigating bugs, root cause analysis

**What it does:**
- Reviews code quality and architecture
- Checks SOLID principles and best practices
- Identifies common bug patterns
- Investigates technical issues
- Performs security and performance reviews
- Documents findings with recommendations

**Example usage:**
```
/review Investigate why the login endpoint is returning 500 errors
```

---

### `/test` - QA Engineer Mode
**Use when:** Writing tests, test plans, coverage analysis

**What it does:**
- Creates comprehensive test plans
- Writes unit, integration, and e2e tests
- Identifies edge cases and boundary conditions
- Analyzes test coverage
- Ensures 80%+ coverage target
- Uses AAA pattern (Arrange, Act, Assert)

**Example usage:**
```
/test Create unit tests for the UserService class
```

---

### `/design` - UI/UX Designer Mode
**Use when:** Reviewing UI, ensuring accessibility, improving UX

**What it does:**
- Reviews application design and usability
- Validates WCAG 2.1 AA accessibility
- Checks color contrast and typography
- Reviews responsive design
- Ensures consistent design language
- Provides actionable recommendations

**Example usage:**
```
/design Review the checkout page for accessibility and UX issues
```

---

### `/architect` - Solution Architect Mode
**Use when:** Designing architecture, making technical decisions

**What it does:**
- Designs scalable system architecture
- Creates technical specifications
- Defines data models and schemas
- Makes technology stack decisions
- Creates ADRs (Architectural Decision Records)
- Plans for security, performance, scalability

**Example usage:**
```
/architect Design a microservices architecture for our e-commerce platform
```

---

### `/analyze` - Business Analyst Mode
**Use when:** Analyzing requirements, creating user stories

**What it does:**
- Analyzes business requirements
- Creates detailed user stories with acceptance criteria
- Defines functional and non-functional requirements
- Prioritizes using MoSCoW method
- Performs gap analysis
- Creates requirements documentation

**Example usage:**
```
/analyze Create user stories for the payment processing feature
```

---

## How to Use

### 1. Type the Command
In Cursor's chat interface, type the command:
```
/implement
```

### 2. Describe Your Task
After the command, describe what you want:
```
/implement Create a REST API for managing blog posts with CRUD operations
```

### 3. AI Switches Context
Cursor AI will:
- Load the command's specialized context
- Read your `.cursorrules` and `memory-bank/` files
- Follow the workflow specific to that command
- Deliver results in that mode's style

---

## Command Comparison with Claude Code Agents

| Cursor Command | Claude Code Agent | Purpose |
|----------------|-------------------|---------|
| `/implement` | fullstack-developer | Full-stack feature implementation |
| `/frontend` | frontend-developer | UI/UX implementation |
| `/backend` | backend-developer | API/database implementation |
| `/review` | principal-engineer | Code review & debugging |
| `/test` | qa-engineer | Testing & QA |
| `/design` | uiux-designer | UI/UX review |
| `/architect` | solution-architect | Architecture design |
| `/analyze` | business-analyst | Requirements analysis |

---

## Tips for Best Results

### 1. Always Start with Context
The commands automatically load your project context from:
- `.cursorrules` - Coding standards
- `memory-bank/` - Project documentation

Make sure these are up-to-date!

### 2. Be Specific
```
❌ Bad:  /implement authentication
✅ Good: /implement JWT-based authentication with refresh tokens using bcrypt for password hashing
```

### 3. Chain Commands
```
1. /analyze Create user stories for social login feature
2. /architect Design the OAuth integration architecture
3. /implement Build the Google OAuth integration
4. /test Create tests for the OAuth flow
5. /review Check the implementation for security issues
```

### 4. Update Memory Bank
After using commands, update your memory bank:
```bash
# Update activeContext.md with what was done
# Update progress.md with completion status
```

---

## Workflow Examples

### Example 1: Building a New Feature

```
1. /analyze
   "Create user stories for the shopping cart feature"

2. /architect
   "Design the shopping cart data model and API structure"

3. /backend
   "Build the shopping cart API endpoints and database schema"

4. /frontend
   "Build the shopping cart UI with add/remove items functionality"

5. /test
   "Create comprehensive tests for the shopping cart functionality"

6. /review
   "Review the shopping cart implementation for performance issues"

7. /design
   "Review the shopping cart UI for accessibility and usability"
```

### Example 2: Fixing a Bug

```
1. /review
   "Investigate why users can't complete checkout"

2. /implement
   "Fix the checkout validation bug identified in the review"

3. /test
   "Add regression tests for the checkout validation"

4. /review
   "Verify the fix doesn't introduce new issues"
```

### Example 3: Improving Code Quality

```
1. /review
   "Analyze the authentication module for technical debt"

2. /test
   "Check test coverage for authentication module"

3. /implement
   "Refactor the authentication code based on review recommendations"

4. /test
   "Increase test coverage to 90%"
```

---

## Customizing Commands

You can edit these command files (`.mmd` files) to:
- Add project-specific guidelines
- Modify workflows
- Add custom checklists
- Include company-specific standards

**Location:** `.cursor/commands/*.mmd`

**Format:**
```markdown
---
name: /command-name
description: Short description
---

Command instructions here...
```

---

## Command File Structure

Each command file follows this structure:

1. **Frontmatter** (YAML)
   - `name`: The slash command name
   - `description`: What the command does

2. **Context Loading**
   - Instructions to read project files
   - What information to gather

3. **Core Responsibilities**
   - What this mode is responsible for
   - Key deliverables

4. **Process/Workflow**
   - Step-by-step approach
   - Checklists and guidelines

5. **Examples**
   - Code examples
   - Best practices
   - Common patterns

6. **Quality Standards**
   - Metrics and targets
   - Quality gates

---

## Integration with Memory Bank

All commands automatically reference:

- **`.cursorrules`**: Project-wide coding standards
- **`memory-bank/projectbrief.md`**: Project goals and scope
- **`memory-bank/systemPatterns.md`**: Architecture patterns
- **`memory-bank/techContext.md`**: Tech stack details
- **`memory-bank/activeContext.md`**: Current work context

This ensures consistent, context-aware assistance!

---

## Troubleshooting

### Command Not Appearing?

1. Check file extension is `.mmd`
2. Check file is in `.cursor/commands/` directory
3. Restart Cursor IDE
4. Check YAML frontmatter is valid

### AI Not Following Command Context?

1. Verify `.cursorrules` exists and is filled in
2. Check `memory-bank/` files are complete
3. Be more specific in your request
4. Try prefacing with: "Following the [command name] workflow..."

### Want to Create Custom Commands?

1. Copy an existing `.mmd` file
2. Modify the frontmatter (name and description)
3. Edit the content to match your needs
4. Save in `.cursor/commands/`
5. Restart Cursor

---

## Best Practices

1. **Keep Commands Focused**: Each command should have a clear, single purpose
2. **Update Regularly**: As your project evolves, update command instructions
3. **Chain Strategically**: Use multiple commands in sequence for complex tasks
4. **Document Outcomes**: After using commands, update `memory-bank/activeContext.md`
5. **Run Quality Gates**: Always run typecheck, lint, test, build after implementation

---

## Contributing

Have improvements to these commands? Want to add new ones?

1. Test your changes locally
2. Document what you changed and why
3. Share with your team
4. Consider contributing back to the boilerplate

---

## Support

- **Documentation**: See main README-CURSOR.md
- **Memory Bank**: See memory-bank/workflows.md
- **Coding Standards**: See .cursorrules

---

**Happy Coding with Cursor Commands!** 🚀


