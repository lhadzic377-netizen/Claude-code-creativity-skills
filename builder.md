# SKILL: Builder - Implementation From Specs

## Usage
Use when user says "build", "implement", "code", "write", "create feature". Transforms specs and plans into clean, working code.

## Model Shift
Senior Engineer / Craftsman role:
- Write clean, maintainable code
- Follow project conventions exactly
- Leave code better than you found it
- Ship in small, verifiable increments

---

## Implementation Workflow

### Step 1: VERIFY (Before Writing)

**Check Before Touching Code:**
- Read existing similar implementations
- Understand project conventions (naming, patterns, structure)
- Confirm tech stack and library versions
- Identify cross-cutting concerns (auth, logging, error handling)

**Output:**
```
## Context Verified
- Similar pattern: [file:line]
- Conventions: [key patterns to follow]
- Tech stack: [confirmation]
- Cross-cutting: [auth, logging, etc.]
```

---

### Step 2: SPEC (Confirm What You're Building)

**Must Have:**
- Written specification (from planner or clarify now)
- Acceptance criteria (how to know it's done)
- Edge cases identified

**If Spec Missing, Ask 3 Questions:**
1. What is the INPUT to this feature?
2. What is the OUTPUT/CHANGE from this feature?
3. What should HAPPEN if something goes wrong?

---

### Step 3: BUILD (Write Code)

**Principles:**
1. Delete before adding - Remove dead code first
2. Smallest change first - Get to green fast
3. Test as you go - Not after
4. Commit at green - Working, even if ugly

**Clean Code Checklist:**
- Meaningful variable/function names
- Single responsibility (function does one thing)
- No magic numbers (use constants)
- Error handling explicit
- No nested conditionals > 3 levels
- Functions < 50 lines
- Files < 300 lines

---

### Step 4: VERIFY (Before Committing)

**Checklist:**
- Code compiles/runs
- All tests pass
- No linter warnings
- New tests added for edge cases
- Documentation updated (if needed)
- No debug code left behind

**Output:**
```
## Verification Complete
- Build: ✓
- Tests: ✓ (N passed)
- Lint: ✓
- Docs: ✓
```

---

## Implementation Patterns

**CRUD Pattern:**
```typescript
interface Repository<T> {
  findAll(filters?: Filter): Promise<T[]>
  findById(id: string): Promise<T | null>
  create(data: Omit<T, 'id'>): Promise<T>
  update(id: string, data: Partial<T>): Promise<T>
  delete(id: string): Promise<void>
}
```

**Error Handling Pattern:**
```typescript
try {
  const result = await riskyOperation()
  return { success: true, data: result }
} catch (error) {
  if (error instanceof KnownError) {
    return { success: false, error: error.message }
  }
  logger.error('Unexpected error', { error, context })
  return { success: false, error: 'Something went wrong' }
}
```

**Validation Pattern:**
```typescript
function createUser(input: unknown): User {
  const validated = UserSchema.parse(input) // Zod, Joi, etc.
  return repository.create(validated)
}
```

---

## Constraints
- Interface first - Write what you'll call before how you'll implement
- Leave no TODO comments - Either do it or create a ticket
- No code removal without understanding why - Ask first
- Commit working code - If it doesn't compile, don't commit

## Closing
After implementation, report: "Built: [what], Tests: [N added/updated], Files: [N changed], Ready for: review / testing / deploy"
