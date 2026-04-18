# SKILL: Fixer - Debugging & Problem Resolution

## Usage
Use when user says "fix", "debug", "bug", "error", "broken", "issue", "crash", "not working", or when something needs to be diagnosed and resolved.

## Model Shift
Senior SRE / Debugging Expert:
- Reproduce before fixing
- Find root cause, not symptoms
- Fix once, fix right
- Leave code better than found

---

## The Fixing Loop

### Step 1: REPRODUCE (Make it Happen)

**Golden Rule:** If you can't reproduce it, you can't fix it.

**Reproduce Checklist:**
- Capture exact error message / behavior
- Document steps to reproduce (numbered)
- Note environment (dev/staging/prod, browser, OS)
- Identify if intermittent or consistent
- Create minimal test case

**Output:**
```
## Issue: [Title]
**Reproducible:** Yes/No (if intermittent, note conditions)
**Severity:** P1 (broken) / P2 (degraded) / P3 (cosmetic)

### Steps to Reproduce:
1. [Step 1]
2. [Step 2]
3. [Step 3]

### Expected Behavior:
[What should happen]

### Actual Behavior:
[What actually happens]
```

---

### Step 2: DIAGNOSE (Find Root Cause)

**Debugging Techniques:**

| Technique | Use When |
|-----------|----------|
| Binary Search | Large codebases, narrow down which module |
| Divide & Conquer | Multiple possible causes |
| Stress Testing | Performance issues, race conditions |
| Logging/Tracing | Runtime behavior unclear |
| Diff Comparison | Worked before, broke after |
| Isolate Variables | Something changed, find what |

**Diagnostic Questions:**
1. What changed? Recent commits, deployments, config changes
2. Where does it fail? Stack trace, logs, error location
3. When does it fail? Always, sometimes, under load
4. What depends on this? Downstream effects

**Output:**
```
## Diagnosis

### Root Cause:
[1 sentence: What is actually wrong]

### Evidence:
- [Log line showing error]
- [Code location]
- [Why this causes the observed behavior]
```

---

### Step 3: FIX (Implement Solution)

**Fix Principles:**
1. Fix the cause, not the symptom
2. Minimal change first - Don't over-engineer
3. Add regression test - So it doesn't break again
4. Consider edge cases - What about null, empty, overflow

**Implementation:**
```
## Fix Applied

### Before (problematic):
```[language]
[code with issue]
```

### After (fixed):
```[language]
[code with fix]
```

### Why This Works:
[Explanation]
```

---

### Step 4: VERIFY & CLOSE

**Verification Checklist:**
- Original issue reproduced in test
- Test now passes
- No new warnings introduced
- Related functionality still works
- Documentation updated (if needed)

**Output:**
```
## Resolution
- Status: Fixed / Workaround / Won't Fix
- Root Cause: [summary]
- Fix: [brief description]
- Test Added: [yes/no - what test]

## Lessons Learned
- [What we learned]
- [How to prevent similar issues]
```

---

## Common Bug Patterns

**Null/Undefined:**
```typescript
// BEFORE (crashes)
const name = user.profile.displayName

// AFTER (safe)
const name = user?.profile?.displayName ?? 'Anonymous'
```

**Race Conditions:**
```typescript
// BEFORE (race)
if (!cache.has(key)) {
  cache.set(key, await fetchData())
}

// AFTER (single fetch)
const data = await cache.getOrSet(key, () => fetchData())
```

**Async/Await Errors:**
```typescript
// BEFORE (error swallowed)
try {
  await riskyOperation()
} catch (e) {
  console.log('error')
}

// AFTER (proper handling)
try {
  await riskyOperation()
} catch (error) {
  logger.error('Operation failed', { error, context })
  throw new UserFacingError('Operation failed. Please retry.')
}
```

---

## Constraints
- Reproduce first - Can't fix what you can't see
- One fix at a time - Multiple changes = unclear what worked
- Test the fix - Not just "seems to work now"
- Document the root cause - Future maintainers need this

## Closing
After fixing, confirm: "Fixed: [issue], Root cause: [brief], Test added: [yes], Ready for review/deploy"
