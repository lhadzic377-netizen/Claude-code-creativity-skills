# SKILL: Planner - Task Breakdown & Execution Planning

## Usage
Use when user says "plan", "break down", "task list", "sprint", "roadmap", "user story", or needs to convert vision into actionable tasks.

## Model Shift
Chief of Staff / Project Manager role:
- Break down big goals into smallest actionable tasks
- Order by dependencies, priority, and risk
- Identify cross-team concerns early
- Estimate complexity and time boxes

---

## The Planning Loop

### Step 1: DISCOVER (Clarify Goal)

**Ask if unclear:**
1. What does success look like? (specific, measurable)
2. What are the constraints? (time, budget, people, tech)
3. Who are the stakeholders? (who decides, who affected)
4. What can't change? (sacred cows, existing systems)

**Output:**
```
## Goal Statement
[1 sentence: What exactly are we building/delivering?]

## Success Criteria
1. [Specific measurable outcome]
2. [Specific measurable outcome]
3. [Specific measurable outcome]

## Constraints
- Time: [X weeks/days]
- Tech: [stack or "flexible"]
- Team: [X people, skills available]
```

---

### Step 2: DECOMPOSE (Break Down)

**Task Hierarchy:**
```
Epic
 └── Feature
      └── User Story / Task
           └── Sub-task
                └── Step
```

**For Each Task, Capture:**
- What: Clear description
- Why: Business value / dependency
- Who: Owner (frontend, backend, design, etc.)
- Size: XS (1-2hr), S (half-day), M (1-2 days), L (3-5 days), XL (week+)
- Risk: Low / Medium / High

**Output:**
```
## Task Breakdown

### Phase 1: Foundation
| # | Task | Owner | Size | Risk | Dependencies |
|---|------|-------|------|------|--------------|
| 1 | [Task] | [Role] | M | Low | None |
| 2 | [Task] | [Role] | S | Low | #1 |

### Phase 2: Core Features
...

### Phase 3: Polish & Launch
...
```

---

### Step 3: SEQUENCE (Order Matters)

**Rules:**
1. Dependencies first - What must be done before what
2. Risk reduction early - Prototype risky parts first
3. Quick wins first - Build momentum
4. Parallel where safe - Independent tracks can run simultaneously

**Critical Path:** Identify longest dependency chain - determines minimum timeline.

**Output:**
```
## Critical Path
1. [Task] → [Task] → [Task] → [Task]
Minimum timeline: X weeks

## Parallel Tracks
Track A: [Task] → [Task]
Track B: [Task] → [Task]
Track C: [Task] (independent)
```

---

### Step 4: REFINE (Sprint-Ready)

**Sprint Backlog Format:**
```
## Sprint 1 (Week 1-2)
### Sprint Goal: [One sentence]
- [ ] [Task #X]: [Description] @[Owner] [X days]
- [ ] [Task #Y]: [Description] @[Owner] [X days]

## Sprint 2 (Week 3-4)
### Sprint Goal: [One sentence]
...
```

---

## Planning Templates

**User Story:**
```
As a [persona],
I want [action],
So that [outcome].

Acceptance Criteria:
- [ ] [Criterion 1]
- [ ] [Criterion 2]
```

**Bug Fix:**
```
## Bug: [Title]
Severity: [P1/P2/P3]
Impact: [Who/what affected]

Root Cause: [If known]
Fix: [Approach]
Tests: [How to verify]
```

---

## Constraints
- Break until smallest deployable units (SDUs)
- No task larger than 5 days - break further
- Always identify done criteria before starting
- Flag when requirements are still unclear

## Closing
After presenting plan, ask: "Does this breakdown match your expectations? What should we adjust?"
