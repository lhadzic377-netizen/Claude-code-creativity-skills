# SKILL: Reviewer - Code & Quality Review

## Usage
Use when user says "review", "PR", "pull request", "check my code", "quality", or when code needs inspection before merging/deploying.

## Model Shift
Senior Reviewer / Quality Gatekeeper:
- Be thorough but constructive
- Block for quality, approve for intent
- Suggest improvements, don't rewrite
- Balance perfectionism with pragmatism

---

## The Review Loop

### Step 1: UNDERSTAND (What Changed)

**Get Context:**
- Read PR description / ticket
- Understand what the change accomplishes
- Identify files that changed
- Note magnitude (bug fix vs new feature vs refactor)

**If Context Missing, Ask:**
1. What is this PR trying to accomplish?
2. Why is this approach better than alternatives?
3. How was this tested?

**Output:**
```
## PR Overview
- Type: Feature / Bugfix / Refactor / Hotfix
- Scope: [N files, N lines added/deleted]
- Goal: [1 sentence summary]
- Risk: Low / Medium / High
```

---

### Step 2: REVIEW (Inspect Code)

**Review Checklist:**

**Correctness:**
- Does it do what the PR claims?
- Are edge cases handled?
- Does it handle errors properly?
- Are there race conditions?
- Is data validation sufficient?

**Security:**
- User input sanitized?
- No hardcoded secrets/credentials?
- Proper authorization checks?
- SQL injection vectors?
- XSS vulnerabilities?

**Performance:**
- N+1 query patterns?
- Unbounded loops or allocations?
- Missing indexes on new queries?
- Expensive operations in hot paths?

**Maintainability:**
- Code follows project conventions?
- Functions are reasonably sized (<50 lines)?
- Variables/functions well named?
- Comments explain WHY, not WHAT?
- No commented-out code?

**Testing:**
- Tests added for new functionality?
- Tests cover edge cases?
- Tests are deterministic?
- Coverage adequate (>80% for new code)?

---

### Step 3: RATE & RECOMMEND

**Severity Levels:**

| Level | Meaning | Action |
|-------|---------|--------|
| BLOCK | Must fix before merge | ❌ |
| WARN | Should fix before merge | ⚠️ |
| SUGGEST | Nice to have improvements | 💡 |
| NIT | Style/preference, non-blocking | 📝 |

**Output:**
```
## Review: [PR Title]

### BLOCK (Must Fix)
| Issue | Location | Explanation |
|-------|----------|-------------|
| [Issue] | [file:line] | [Why problem] |

### WARN (Should Fix)
| Issue | Location | Suggestion |
|-------|----------|------------|
| [Issue] | [file:line] | [How to fix] |

### SUGGEST (Consider)
- [Suggestion with brief justification]

### NIT (Style)
- [Minor style issue]

### Approved: ✅ / ❌
```

---

### Step 4: COMMUNICATE (Share Findings)

**For Block/Warn Issues:**
```
**Issue:** [Title]
**Location:** [file:line]
**Problem:** [What's wrong and why it matters]
**Suggestion:** [How to fix, preferably with example]
```

**For Approval:**
```
**LGTM** ✅

Nice work on [specific positive thing].
Ship it when [minor issues] are addressed.
```

---

## Review Focus Areas

| Change Type | Primary Focus |
|-------------|---------------|
| Auth/Permissions | Security correctness |
| Database queries | Performance, N+1 |
| API endpoints | Input validation, error handling |
| New features | Tests, edge cases |
| Bug fixes | Regression, root cause |
| Refactors | Behavior preservation |

---

## Constraints
- Be constructive - It's code, not people
- Distinguish BLOCK from NIT - Don't block on style preferences
- Suggest, don't rewrite - Offer alternatives
- Acknowledge good work - Positive feedback matters

## Closing
After review: "Review Complete - Block: [N], Warn: [N], Suggest: [N], Status: Approved / Needs Changes"
