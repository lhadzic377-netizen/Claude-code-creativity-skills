# SKILL: Tester - Test Strategy & Implementation

## Usage
Use when user says "test", "TDD", "coverage", "unit test", "integration test", "e2e", or when testing strategy needs to be defined/implemented.

## Model Shift
QA Engineer / Test Architect:
- Test behavior, not implementation
- Cover happy path AND edge cases
- Tests must be deterministic
- Write tests that give confidence

---

## Test Strategy

### Test Pyramid:

```
        ┌─────┐
        │ E2E │  ← Few, slow, high confidence
       ┌┴─────┴┐
       │Integration│ ← Some, medium speed
      ┌┴────────┴┐
      │  Unit   │  ← Many, fast, isolated
      └─────────┘
```

**Test Types:**

| Type | Purpose | Speed | Quantity |
|------|---------|-------|----------|
| Unit | Test single function/class | < 10ms | Many |
| Integration | Test component interactions | < 1s | Some |
| E2E | Test full user flows | Minutes | Few |

**Output:**
```
## Test Strategy

### Coverage Target: 80%+

### Unit Tests (N%)
- What: [functions, utilities, business logic]
- Mock: [external dependencies]

### Integration Tests (N%)
- What: [API endpoints, DB operations]
- Real: [actual dependencies]

### E2E Tests (N%)
- What: [critical user journeys]
- Environment: [staging/prod-like]
```

---

## Write Tests (TDD Approach)

**Red-Green-Refactor:**
1. RED: Write failing test first
2. GREEN: Write minimal code to pass
3. REFACTOR: Improve code, keep tests green

**AAA Pattern:**
```typescript
test('calculates total correctly', () => {
  // Arrange - set up test data
  const order = { items: [{ price: 10 }, { price: 20 }] }

  // Act - execute what we're testing
  const total = calculateTotal(order)

  // Assert - verify results
  expect(total).toBe(30)
})
```

**Test Naming:** [what it tests]

```typescript
// GOOD
test('returns empty array when no items match filter')
test('throws ValidationError when email is invalid')
test('falls back to cache when Redis is unavailable')

// BAD
test('test1')
test('handleError')
```

---

## Cover Edge Cases

**Edge Case Checklist:**

| Category | Cases to Consider |
|----------|-------------------|
| Input | Empty, null, undefined, valid, invalid |
| Boundaries | Min, max, boundary + 1, boundary - 1 |
| Types | Wrong type passed |
| Order | Empty first, single item, many items |
| State | Already exists, doesn't exist, modified |
| Errors | Network failure, timeout, permission denied |

**Example Test Suite:**
```typescript
describe('createUser', () => {
  test('creates user with valid data', () => { /* ... */ })
  test('throws when email is missing', () => { /* ... */ })
  test('throws when email is invalid format', () => { /* ... */ })
  test('throws when email already exists', () => { /* ... */ })
  test('hashes password before storing', () => { /* ... */ })
})
```

---

## Verify & Report

**Run Tests:**
```bash
npm test -- --coverage
```

**Coverage Report:**
```
## Test Coverage

File              | % Stmts | % Branch | % Funcs | % Lines |
------------------|---------|----------|---------|---------|
src/users.ts      |  100    |   100    |   100   |   100   |
src/orders.ts     |   85    |    75    |    80   |    85   |

OVERALL         |   82    |    78    |    79   |    82   |
```

**Checklist:**
- All tests pass
- Coverage target met (>80%)
- No flaky tests (run 3x to verify)
- CI pipeline green

---

## Test Patterns

**Mocking External Dependencies:**
```typescript
const mockDb = {
  findById: jest.fn(),
  create: jest.fn(),
}

jest.useFakeTimers()
jest.setSystemTime(new Date('2024-01-01'))
```

**Async Testing:**
```typescript
test('resolves with data on success', async () => {
  const result = await fetchUser(1)
  expect(result).toEqual({ id: 1, name: 'Test' })
})

test('rejects with error on failure', async () => {
  await expect(fetchUser(999)).rejects.toThrow('User not found')
})
```

---

## Constraints
- Test behavior, not implementation - Refactor without breaking tests
- Deterministic only - No flaky tests
- Isolate tests - Each test independent
- Fast feedback - Unit tests < 10ms each

## Closing
After testing: "Test Coverage: [N]%, Tests Added: [N], Status: Ready / Needs More Tests"
