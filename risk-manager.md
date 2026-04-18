# SKILL: Risk Manager - Risk Identification & Mitigation

## Usage
Use when user says "risk", "mitigate", "contingency", "what if", "could go wrong", or when planning decisions with uncertain outcomes.

## Model Shift
Risk Analyst / SRE Mindset:
- Assume things WILL fail
- Identify failure modes before they happen
- Plan recovery, not just prevention
- Communicate risks clearly to stakeholders

---

## Risk Management Loop

### Step 1: IDENTIFY (What Could Go Wrong)

**Risk Categories:**

| Category | Examples |
|----------|----------|
| Technical | Data loss, performance degradation, security breach, dependency failure |
| People | Key person dependency, skill gaps, team availability |
| Process | Approval delays, handoff bottlenecks, communication gaps |
| External | Vendor lock-in, regulatory changes, market shifts |
| Scope | Feature creep, requirement changes, integration complexity |

**Brainstorm Questions:**
- What if this dependency fails?
- What if this team member leaves?
- What if we underestimated this by 10x?
- What if regulatory environment changes?
- What if competitors ship first?

**Output:**
```
## Identified Risks

| Risk | Category | Impact | Likelihood |
|------|----------|--------|------------|
| [Description] | [Type] | High/Med/Low | High/Med/Low |
```

---

### Step 2: ASSESS (Prioritize Risks)

**Risk Matrix:**
```
                 Likelihood
              Low    Med    High
         ┌─────────────────────┐
    High │ MEDIUM  HIGH   HIGH │
Impact   ├─────────────────────┤
    Med  │  LOW   MEDIUM  HIGH │
         ├─────────────────────┤
    Low  │  LOW    LOW   MEDIUM|
         └─────────────────────┘
```

**Prioritization Rules:**
1. HIGH Impact + HIGH Likelihood → Mitigate immediately
2. HIGH Impact + MED Likelihood → Mitigate or contingency
3. MEDIUM both → Plan contingency
4. LOW either → Accept or monitor

---

### Step 3: MITIGATE (Plan Actions)

**Mitigation Strategies:**

| Strategy | When to Use |
|----------|-------------|
| Eliminate | Remove the risk source entirely |
| Reduce | Lower likelihood or impact |
| Transfer | Insurance, contracts, shared risk |
| Accept | Low impact, unlikely, cost > benefit |
| Monitor | Track for early warning signs |

**For Each HIGH/MEDIUM Risk:**
```
## Risk: [Name]
- Impact: [What happens if it occurs]
- Likelihood: [Why likely/unlikely]
- Mitigation: [Specific action to reduce]
- Owner: [Who is responsible]
- Deadline: [When mitigation complete]
```

---

### Step 4: CONTINGENCY (Plan B)

**For Critical Risks:**
```
## Contingency Plan: [Risk Name]

### Trigger (When to Activate):
[Specific condition or metric threshold]

### Response Steps:
1. [First action]
2. [Second action]
3. [Communication plan]

### Rollback:
[How to revert if deployment-related]

### Communication:
- Internal: [who notifies who]
- External: [customer notification if applicable]
```

---

## Constraint Planning

**Hard Constraints (Must Not Break):**
- Security requirements
- Compliance (GDPR, SOC2, etc.)
- Data integrity rules
- SLA commitments

**Soft Constraints (Stretch Goals):**
- Timeline preferences
- Feature completeness
- Performance targets
- Cost optimization

**Output:**
```
## Constraints Map

### Hard Lines (Never Cross)
□ [Constraint with justification]

### Soft Lines (Negotiable)
□ [Constraint with flexibility range]
```

---

## Constraints
- No risk is zero - Always have a contingency
- Communicate up - Leadership needs to know HIGH risks
- Document triggers - Specific conditions, not feelings
- Review regularly - Risks change as work progresses

## Closing
After presenting risks, ask: "Which risks should we prioritize for mitigation? Any we're comfortable accepting?"
