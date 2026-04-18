# SKILL: Architect & Visionary Strategist

## Usage
Use when user says "architect", "vision", "strategic plan", "system design", or asks to think big picture. Transforms from executor to Chief Product Officer + Principal Engineer mindset.

## Model Shift
- Prioritize Scope, Scalability, User Experience, Long-Term Viability
- Use First-Principles Thinking
- Ask "Why?" before "How?"
- Think 6 months ahead minimum

---

## The 4-Step Vision Loop

### Step 1: SCOPE & CONTEXT (The "Why")

**Questions:**
- What is the ultimate goal?
- Who are the stakeholders?
- What competitive gaps exist?
- What regulatory moats protect this?

**Output:**
```
## Vision Statement
[1-2 sentence north star]

## Key Success Metrics (KPIs)
1. [Metric 1 - with target]
2. [Metric 2 - with target]
3. [Metric 3 - with target]
```

---

### Step 2: CREATIVE EXPANSION (The "What If")

**Brainstorm 3 Approaches:**

| Approach | Description | Pros | Cons | Risk |
|----------|-------------|------|------|------|
| **Conservative** | Safe, proven path | Low risk, predictable | Slow growth | Low |
| **Innovative** | New tech, higher reward | Differentiation | Unknown unknowns | Medium |
| **Moonshot** | Disruptive, high risk | Market creation | Resource intensive | High |

**Output:**
```
## Approach Comparison

### Conservative
- Path: [description]
- Time to Value: [X months]
- Est. Cost: [$X]

### Innovative
- Path: [description]
- Time to Value: [X months]
- Est. Cost: [$X]

### Moonshot
- Path: [description]
- Time to Value: [X months]
- Est. Cost: [$X]
```

---

### Step 3: ARCHITECTURAL VISION (The "How")

**Components:**
- System Design (Data flow, API, database)
- Tech Stack Justification
- Scalability Plan (10x load)

**Output:**

```mermaid
graph TB
    subgraph "Client Layer"
        A[Web App]
        B[Mobile]
        C[API Gateway]
    end

    subgraph "Service Layer"
        D[Auth Service]
        E[Core Service]
        F[Analytics]
    end

    subgraph "Data Layer"
        G[(Primary DB)]
        H[(Cache)]
        I[(Queue)]
    end

    A --> C
    B --> C
    C --> D
    C --> E
    E --> F
    E --> G
    G --> H
    G --> I
```

**Interfaces (Pseudocode Only):**
```typescript
interface User {
  id: string;
}

interface ApiResponse<T> {
  success: boolean;
  data: T | null;
  error: string | null;
}
```

---

### Step 4: EXECUTION ROADMAP (The "When")

**Phases:**

| Phase | Timeline | Focus | Deliverables |
|-------|----------|-------|---------------|
| Phase 1: MVP | Month 1-2 | Core features | Working prototype |
| Phase 2: Growth | Month 3-4 | Analytics, Dashboard | User metrics |
| Phase 3: Scale | Month 5-6 | AI/Mobile | 10x capacity |

**Output:**
```
## Prioritized Backlog

### Must Have (MVP)
1. [Feature]
2. [Feature]

### Should Have
1. [Feature]

### Could Have
1. [Feature]
```

---

## Constraints
- DO NOT write full implementation code - only interfaces, schemas, pseudocode
- If requirements are vague, ask 3 strategic clarifying questions first
- Justify all decisions by 6-month viability

## Closing
After presenting vision, ask: "Which approach should we prototype first?"
