# DevOps Agent Skills

Transform Claude Code or OpenClaw from a code generator into a **full development team**. 9 specialized skills covering every phase of the development lifecycle.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

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

## Development Workflow

```
┌─────────────┐
│  Architect  │ ← Strategic vision, system design, Mermaid diagrams
└──────┬──────┘
       ▼
┌─────────────┐
│   Planner   │ ← Task breakdown, sprint backlogs, dependencies
└──────┬──────┘
       ▼
┌─────────────┐
│  Designer   │ ← API specs, data models, interfaces
└──────┬──────┘
       ▼
┌─────────────┐
│   Builder   │ ← Clean code, tests, error handling
└──────┬──────┘
       ▼
┌─────────────┐
│  Reviewer   │ ← Security, quality, BLOCK/WARN/SUGGEST
└──────┬──────┘
       ▼
┌─────────────┐
│   Tester    │ ← TDD, 80%+ coverage, unit/integration/E2E
└──────┬──────┘
       ▼
┌─────────────┐
│   Fixer     │ ← Root cause analysis, reproducible bugs
└──────┬──────┘
       ▼
┌─────────────┐
│  Deployer   │ ← Blue/green, canary, rollback, monitoring
└─────────────┘
```

## Installation

### Download

Download `devops-agent-skills.zip` from this repo.

### Claude Code

```bash
unzip devops-agent-skills.zip
cp -r architect-skill/claude-code/* ~/.claude/skills/
```

### OpenClaw

```bash
unzip devops-agent-skills.zip
cp -r architect-skill/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
openclaw gateway restart
```

### OpenClaw Agent Setup

Add skills to your agent's `agent.json`:

```json
{
  "skills": [
    "architect",
    "planner",
    "builder",
    "designer",
    "reviewer",
    "tester",
    "fixer",
    "risk-manager",
    "deployer"
  ]
}
```

Then restart: `openclaw gateway restart`

## Usage Examples

```
You: /architect betting research platform
AI: [4-Step Vision Loop]
    - Vision Statement + 3 KPIs
    - Conservative/Innovative/Moonshot comparison
    - Mermaid architecture diagram
    - Phased roadmap
AI: "Which approach should we prototype first?"

You: /plan MVP for conservative approach
AI: [Task breakdown with sprint backlog]
    - Critical path identified
    - Owner assignments
    - Sprint 1, 2, 3 defined

You: /design user authentication API
AI: [API specification]
    - REST endpoints with schemas
    - Request/response types
    - Error codes
    - Data model

You: /build user authentication
AI: [Implementation]
    - Clean code from spec
    - Unit tests
    - Ready for review

You: /review authentication implementation
AI: [Code review]
    - BLOCK/WARN/SUGGEST ratings
    - Security scan
    - Edge case analysis

You: /test authentication
AI: [Test suite]
    - 80%+ coverage
    - Unit + integration tests
    - E2E smoke tests

You: /fix login returning 500
AI: [Debugging]
    - Issue reproduced
    - Root cause found
    - Fix with regression test

You: /deploy to production
AI: [Safe deployment]
    - Pre-deploy checks
    - Blue/green strategy
    - Rollback plan ready
```

## Directory Structure

```
devops-agent-skills/
├── README.md
├── devops-agent-skills.zip    # Download this
├── claude-code/              # Claude Code skills
│   ├── architect.md
│   ├── planner.md
│   ├── designer.md
│   ├── builder.md
│   ├── reviewer.md
│   ├── tester.md
│   ├── fixer.md
│   ├── risk-manager.md
│   └── deployer.md
└── openclaw/                 # OpenClaw skills
    ├── architect.md
    ├── planner.md
    ├── designer.md
    ├── builder.md
    ├── reviewer.md
    ├── tester.md
    ├── fixer.md
    ├── risk-manager.md
    └── deployer.md
```

## Platform Support

| Platform | Format | Install Location |
|----------|--------|-----------------|
| Claude Code | YAML frontmatter | `~/.claude/skills/` |
| OpenClaw | Simple markdown | `~/.openclaw/agents/AGENT/agent/skills/` |

## Skill Details

### Architect
Strategic system design with 4-Step Vision Loop. Creates vision statements, KPIs, approach comparisons (Conservative/Innovative/Moonshot), Mermaid diagrams, and phased roadmaps.

### Planner
Task breakdown and sprint planning. Converts goals to actionable backlogs, identifies critical paths, sequences dependencies, estimates sizes (XS-XL).

### Designer
API, data model, and interface design. Creates REST specs, TypeScript interfaces, database schemas, and component contracts.

### Builder
Implementation from specs. Writes clean, maintainable code with tests, proper error handling, and project convention adherence.

### Reviewer
Code quality gatekeeper. Rates issues BLOCK/WARN/SUGGEST/NIT. Checks correctness, security, performance, and maintainability.

### Tester
Test strategy and TDD implementation. Sets up test pyramids, ensures 80%+ coverage, writes unit/integration/E2E tests.

### Fixer
Systematic debugging. Reproduces issues, finds root causes, implements fixes, adds regression tests.

### Risk Manager
Proactive risk identification. Categorizes technical/people/process/external risks, creates mitigation plans and contingencies.

### Deployer
Safe deployment orchestration. Blue/green and canary strategies, rollback procedures, smoke tests, post-deploy monitoring.

## Requirements

- **Claude Code:** Claude Code CLI
- **OpenClaw:** OpenClaw CLI with configured agent
- Mermaid.js (for diagram rendering in compatible environments)

## License

MIT License - feel free to use, modify, and distribute.
