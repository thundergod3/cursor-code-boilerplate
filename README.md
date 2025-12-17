# Cursor AI Boilerplate

> **Universal coding standards and agent-based workflows for Cursor AI projects**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 🎯 What is This?

This boilerplate provides a complete, production-ready structure for projects using **Cursor AI**, converted from Claude Code. It includes:

✅ **`.cursorrules`** - Comprehensive coding standards and AI guidance  
✅ **`memory-bank/`** - Structured documentation system for project context  
✅ **`.cursor/commands/`** - Specialized AI commands (agents) for different workflows  
✅ **Multi-language support** - TypeScript, Python, Go, Rust patterns  
✅ **Quality-first approach** - TDD, type safety, security best practices  
✅ **Modern tech stacks** - Latest frameworks and tools (2023-2025)

---

## 🚀 Quick Start

### 1. Copy to Your Project

```bash
# Copy .cursorrules
cp .cursorrules /path/to/your/project/

# Copy memory-bank directory
cp -r memory-bank /path/to/your/project/

# Copy Cursor commands
cp -r .cursor /path/to/your/project/
```

### 2. Customize `.cursorrules`

Replace all `{{PLACEHOLDER}}` values with your project specifics:

```bash
{{VERSION}}              # e.g., "1.0.0"
{{DATE}}                 # e.g., "2025-12-17"
{{LANGUAGE}}             # e.g., "TypeScript"
{{PACKAGE_MANAGER}}      # e.g., "pnpm"
{{BACKEND_FRAMEWORK}}    # e.g., "Hono"
{{FRONTEND_FRAMEWORK}}   # e.g., "React"
{{DATABASE_ORM}}         # e.g., "Drizzle"
{{TESTING_FRAMEWORK}}    # e.g., "Vitest"
{{LINTER_FORMATTER}}     # e.g., "Biome"
```

### 3. Fill in Memory Bank

Complete the template files in `memory-bank/`:
1. `projectbrief.md` - Project goals, scope, constraints
2. `productContext.md` - User needs, features, roadmap
3. `systemPatterns.md` - Architecture, patterns, decisions
4. `techContext.md` - Tech stack, setup, configuration
5. `activeContext.md` - Current work, recent changes
6. `progress.md` - Status, completed work, next steps

### 4. Use Cursor Commands

Start using specialized AI modes:

```
/implement - Full-stack developer mode
/review    - Code review and debugging mode
/test      - QA and testing mode
/design    - UI/UX review mode
/architect - Architecture design mode
/analyze   - Requirements analysis mode
```

---

## 📁 Structure

```
your-project/
├── .cursorrules              # Cursor AI rules and standards
├── .cursor/
│   └── commands/             # Specialized AI commands
│       ├── implement.mmd     # Developer mode
│       ├── review.mmd        # Review mode
│       ├── test.mmd          # Testing mode
│       ├── design.mmd        # UI/UX mode
│       ├── architect.mmd     # Architecture mode
│       ├── analyze.mmd       # Analysis mode
│       └── README.md         # Commands documentation
├── memory-bank/              # Project documentation
│   ├── projectbrief.md      # Project foundation
│   ├── productContext.md    # Product details
│   ├── systemPatterns.md    # Architecture patterns
│   ├── techContext.md       # Tech stack details
│   ├── activeContext.md     # Current work context
│   ├── progress.md          # Progress tracking
│   └── workflows.md         # Development workflows
├── src/                     # Your source code
├── tests/                   # Your tests
└── [your project files]
```

---

## 🎨 Features

### 1. Cursor Commands (Agent-Based Workflows)

Specialized AI modes for different tasks:

| Command | Purpose | Use When |
|---------|---------|----------|
| `/implement` | Build features, APIs, UI | Coding new functionality |
| `/review` | Code review, debugging | Investigating issues |
| `/test` | Write tests, coverage | Ensuring quality |
| `/design` | UI/UX review | Improving user experience |
| `/architect` | System design | Making architectural decisions |
| `/analyze` | Requirements | Defining user stories |

**Example:**
```
/implement Create a user authentication API with JWT tokens
/test Create comprehensive tests for the authentication flow
/review Check the implementation for security vulnerabilities
```

### 2. Memory Bank System

Cursor AI reads these files before every task:
- Project context and goals
- Architecture patterns
- Current work status
- Tech stack details
- Recent changes

**Result:** AI that deeply understands your project!

### 3. Quality Standards

Built-in standards for:
- ✅ Test-Driven Development (TDD)
- ✅ SOLID principles
- ✅ Security best practices
- ✅ Performance optimization
- ✅ Accessibility (WCAG 2.1 AA)
- ✅ Type safety (no `any` types)

### 4. Multi-Language Support

Pre-configured patterns for:
- **TypeScript/JavaScript** - React, Hono, Elysia, Drizzle, Vitest
- **Python** - FastAPI, SQLAlchemy, Pydantic, pytest
- **Go** - Gin, GORM, testify
- **Rust** - Axum, SeaORM, cargo test

### 5. Git Workflow

- Branch naming conventions
- Conventional commits
- Protected branch rules
- Quality gates (never skip!)

---

## 🎯 How It Works

### Before ANY Task

Cursor AI automatically:
1. Reads `.cursorrules` for coding standards
2. Reads `memory-bank/` files for project context
3. Uses the appropriate command mode (if specified)
4. Follows established patterns

### After EVERY Change

You should:
1. Update `memory-bank/activeContext.md`
2. Update `memory-bank/progress.md`
3. Run quality gates
4. Update `.cursorrules` if new patterns emerge

### Quality Gates (Never Skip!)

```bash
npm run typecheck   # Type checking
npm run lint        # Linting
npm run test        # Tests
npm run build       # Build verification
```

**These MUST pass before every commit. No exceptions.**

---

## 📚 Documentation

### Core Files

- **[README-CURSOR.md](./README-CURSOR.md)** - Complete Cursor-specific guide
- **[.cursorrules](./.cursorrules)** - Coding standards and AI guidance
- **[.cursor/commands/README.md](./.cursor/commands/README.md)** - Commands documentation

### Memory Bank

- **[projectbrief.md](./memory-bank/projectbrief.md)** - Project foundation
- **[productContext.md](./memory-bank/productContext.md)** - Product details
- **[systemPatterns.md](./memory-bank/systemPatterns.md)** - Architecture patterns
- **[techContext.md](./memory-bank/techContext.md)** - Tech stack
- **[activeContext.md](./memory-bank/activeContext.md)** - Current work
- **[progress.md](./memory-bank/progress.md)** - Project status
- **[workflows.md](./memory-bank/workflows.md)** - Development workflows

---

## 🔥 Key Principles

### 1. Context is King
Memory bank ensures Cursor AI always has full project context.

### 2. Quality First
- TDD mandatory
- 80%+ test coverage
- Type safety everywhere
- All inputs validated

### 3. Modern Stack Only
- Technologies from 2023-2025
- Active maintenance required
- Type-first approach

### 4. Security by Default
- Input validation everywhere
- Parameterized queries only
- Environment variables for secrets
- HTTPS/TLS in production

---

## 🤝 Compared to Claude Code

This boilerplate is **adapted from Claude Code** for Cursor:

| Feature | Claude Code | Cursor (This) |
|---------|-------------|---------------|
| Configuration | `CLAUDE.md` | `.cursorrules` |
| Agents | `.claude/agents/*.md` | `.cursor/commands/*.mmd` |
| Documentation | `.claude/docs/` | `memory-bank/` |
| Context System | Manual agent switching | Unified AI + commands |

**Key Difference:** Cursor uses a single AI with specialized command modes, vs Claude Code's separate agents.

---

## 💡 Example Workflows

### Building a New Feature

```bash
# 1. Analyze requirements
/analyze Create user stories for the shopping cart feature

# 2. Design architecture
/architect Design the shopping cart data model and API

# 3. Implement
/implement Build the shopping cart API endpoints

# 4. Test
/test Create comprehensive tests for shopping cart

# 5. Review
/review Check for performance and security issues

# 6. UI/UX
/design Review shopping cart UI for accessibility
```

### Fixing a Bug

```bash
# 1. Investigate
/review Investigate why users can't complete checkout

# 2. Fix
/implement Fix the checkout validation bug

# 3. Test
/test Add regression tests for checkout validation

# 4. Verify
/review Verify the fix doesn't introduce new issues
```

---

## 📦 What's Included

```
claude-code-boilerplate/
├── .cursorrules              # Cursor AI rules
├── .cursor/
│   └── commands/             # 6 specialized commands
│       ├── implement.mmd
│       ├── review.mmd
│       ├── test.mmd
│       ├── design.mmd
│       ├── architect.mmd
│       ├── analyze.mmd
│       └── README.md
├── memory-bank/              # Documentation structure
│   ├── projectbrief.md
│   ├── productContext.md
│   ├── systemPatterns.md
│   ├── techContext.md
│   ├── activeContext.md
│   ├── progress.md
│   └── workflows.md
├── .claude/agents/           # Original Claude Code agents (reference)
├── CLAUDE.md                 # Original Claude Code template (reference)
├── README-CURSOR.md         # Detailed Cursor guide
├── README.md                # This file
└── LICENSE
```

---

## 🎓 Getting Started

1. **Read** [README-CURSOR.md](./README-CURSOR.md) for complete guide
2. **Copy** `.cursorrules` and `memory-bank/` to your project
3. **Copy** `.cursor/commands/` to enable specialized modes
4. **Fill in** all `{{PLACEHOLDERS}}` in `.cursorrules`
5. **Complete** memory-bank template files
6. **Start** using Cursor commands!

---

## 🚨 Important Reminders

### ❌ Never Skip Quality Gates
```bash
typecheck → lint → test → build
```
All must pass before commit. No `--no-verify`.

### ✅ Always Update Memory Bank
After every significant change:
- Update `activeContext.md`
- Update `progress.md`
- Update `.cursorrules` if patterns change

### 🎯 Replace ALL Placeholders
Don't leave `{{PLACEHOLDERS}}` - AI follows generic patterns if you do.

### 🗑️ Delete Unused Sections
Remove language sections you don't use from `.cursorrules`.

---

## 📄 License

MIT License - Use freely in your projects!

---

## 🙏 Credits

**Adapted from Claude Code boilerplate for Cursor AI**

Key adaptations:
- Single `.cursorrules` file
- Cursor commands for agent workflows
- Unified memory-bank structure
- Simplified workflow patterns

---

## 📞 Support

- **Issues:** Open an issue on GitHub
- **Questions:** Check [README-CURSOR.md](./README-CURSOR.md)
- **Commands:** See [.cursor/commands/README.md](./.cursor/commands/README.md)

---

## 🎉 Happy Coding!

With this boilerplate, Cursor AI becomes a true pair programming partner that:
- 🧠 Understands your project deeply
- 🎯 Follows established patterns
- ✨ Maintains quality standards
- 🚀 Helps you ship faster

**Now go build something amazing!** 🚀

---

### Quick Links

- [Complete Cursor Guide](./README-CURSOR.md)
- [Commands Documentation](./.cursor/commands/README.md)
- [Original Claude Code Template](./CLAUDE.md)


