# DevOps Agent Skill Family

A comprehensive suite of Claude Code skills that transform AI from a code generator into a **full development team**.

## The Skill Family

| Skill | Trigger | Role |
|-------|---------|------|
| **Architect** | `/architect [topic]` | Chief Product Officer + Principal Engineer |
| **Planner** | `/plan [goal]` | Chief of Staff / Project Manager |
| **Designer** | `/design [feature]` | Principal Designer / Architect |
| **Builder** | `/build [feature]` | Senior Engineer / Craftsman |
| **Reviewer** | `/review [PR]` | Senior Reviewer / Quality Gatekeeper |
| **Tester** | `/test [feature]` | QA Engineer / Test Architect |
| **Fixer** | `/fix [issue]` | Senior SRE / Debugging Expert |
| **Risk Manager** | `/risk [plan]` | Risk Analyst / SRE Mindset |
| **Deployer** | `/deploy [target]` | DevOps Engineer / Release Manager |

## Workflow

```
┌─────────────┐
│  Architect  │ ← Strategic vision, system design
└──────┬──────┘
       ▼
┌─────────────┐
│   Planner   │ ← Task breakdown, sprint planning
└──────┬──────┘
       ▼
┌─────────────┐
│  Designer   │ ← API design, data models, schemas
└──────┬──────┘
       ▼
┌─────────────┐
│   Builder   │ ← Implementation, clean code
└──────┬──────┘
       ▼
┌─────────────┐
│  Reviewer   │ ← Code review, quality gates
└──────┬──────┘
       ▼
┌─────────────┐
│   Tester    │ ← Test strategy, TDD, coverage
└──────┬──────┘
       ▼
┌─────────────┐
│   Fixer     │ ← Debugging, root cause analysis
└──────┬──────┘
       ▼
┌─────────────┐
│  Deployer   │ ← CI/CD, deployment, rollback
└─────────────┘
```

## Directory Structure

```
devops-agent-skills/
├── README.md
├── architect/
│   └── SKILL.md
├── planner/
│   └── SKILL.md
├── builder/
│   └── SKILL.md
├── designer/
│   └── SKILL.md
├── reviewer/
│   └── SKILL.md
├── tester/
│   └── SKILL.md
├── fixer/
│   └── SKILL.md
├── risk-manager/
│   └── SKILL.md
└── deployer/
    └── SKILL.md
```

## Installation

### Option 1: Clone and Copy All

```bash
# Clone this repo
git clone https://github.com/YOUR_USERNAME/devops-agent-skills.git

# Copy all skills to Claude Code
cp -r architect planner builder designer risk-manager fixer reviewer tester deployer ~/.claude/skills/
```

### Option 2: Per-Skill

Copy only what you need:

```bash
cp -r architect ~/.claude/skills/
cp -r planner ~/.claude/skills/
# etc.
```

## Usage

```
You: /architect Agent research platform
AI: [Runs 4-Step Vision Loop]
    - Vision Statement + 3 KPIs
    - Conservative/Innovative/Moonshot comparison
    - Mermaid architecture diagram
    - Phased roadmap
AI: "Which approach should we prototype first?"

You: /plan MVP for conservative approach
AI: [Breaks down into sprint backlog]
    - Task breakdown with owners
    - Critical path identified
    - Sprint 1, 2, 3 defined

You: /design user authentication API
AI: [Creates API specification]
    - REST endpoints
    - Request/Response schemas
    - Error codes
    - Data model

You: /build user authentication
AI: [Implements from spec]
    - Clean code following conventions
    - Tests added
    - Ready for review

You: /review authentication implementation
AI: [Reviews code]
    - BLOCK/WARN/SUGGEST ratings
    - Security checks
    - Edge cases checked

You: /test authentication
AI: [Sets up test strategy]
    - Unit tests (80%+ coverage)
    - Integration tests
    - E2E smoke tests

You: /fix login returning 500
AI: [Debugs systematically]
    - Reproduces issue
    - Finds root cause
    - Applies fix with test

You: /deploy to production
AI: [Deploys safely]
    - Pre-deploy checks
    - Blue/green or canary deploy
    - Smoke tests
    - Rollback plan ready
```

## Skill Descriptions

### Architect
Strategic thinking and system design. Creates high-level vision, compares approaches (Conservative/Innovative/Moonshot), designs architecture with Mermaid diagrams, and defines execution roadmaps.

### Planner
Task breakdown and sprint planning. Converts goals into actionable tasks, identifies dependencies, sequences work, and creates sprint backlogs.

### Designer
API, data model, and interface design. Creates schemas, defines REST endpoints, designs database structures, and specifies UI components.

### Builder
Implementation from specs. Writes clean, maintainable code following project conventions, with tests and proper error handling.

### Reviewer
Code review and quality assurance. Inspects PRs for correctness, security, performance, and maintainability. Rates issues BLOCK/WARN/SUGGEST/NIT.

### Tester
Test strategy and implementation. Sets up test pyramids, writes unit/integration/E2E tests, and ensures >80% coverage.

### Fixer
Debugging and problem resolution. Reproduces issues, finds root causes, implements fixes, and adds regression tests.

### Risk Manager
Risk identification and mitigation. Identifies technical/people/process/external risks, assesses likelihood and impact, and creates contingency plans.

### Deployer
Deployment and release management. Executes blue/green, canary, or direct deployments with rollback plans and post-deploy monitoring.

## Requirements

- Claude Code CLI
- Mermaid.js support (for diagrams in compatible renderers)

## License

MIT
