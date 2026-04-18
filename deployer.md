# SKILL: Deployer - Deployment & Release Management

## Usage
Use when user says "deploy", "release", "ship", "push to prod", "rollback", "CI/CD", or when code needs to go to production/staging.

## Model Shift
DevOps Engineer / Release Manager:
- Minimize risk per deployment
- Maximize confidence before push
- Have rollback plan ready
- Communicate changes clearly

---

## Deployment Workflow

### Step 1: PREPARE (Before Building)

**Pre-Deploy Checklist:**
- All tests passing (CI green)
- Code reviewed and approved
- Changelog updated
- Version bumped (if applicable)
- Migration scripts ready (if DB changes)
- Feature flags configured (if new features)
- Rollback plan documented

**Output:**
```
## Pre-Deploy Checklist

- [x] Tests: 247 passed
- [x] Coverage: 84%
- [x] Review: Approved by @alice
- [x] Changelog: Updated
- [x] Version: 2.1.0
- [ ] Migration: Not needed
- [ ] Feature Flags: N/A
- [ ] Rollback: [plan documented]
```

---

### Step 2: BUILD (Compile & Package)

```bash
# 1. Clean
npm ci

# 2. Lint
npm run lint

# 3. Type check
npm run typecheck

# 4. Test
npm test

# 5. Build
npm run build

# 6. Package
docker build -t myapp:2.1.0 .
docker tag myapp:2.1.0 myapp:latest
```

**Output:**
```
## Build Complete

- Version: 2.1.0
- Image Size: 145MB
- Build Time: 2m 34s
- Artifacts: myapp:2.1.0, myapp:latest
```

---

### Step 3: DEPLOY (Push to Target)

**Environment Progression:**
```
Dev → Staging → Production
 (fast)    (mirror)   (careful)
```

**Deployment Strategies:**

| Strategy | When to Use | Risk |
|----------|-------------|------|
| Direct | Hotfixes, low risk | High |
| Blue/Green | Zero downtime desired | Medium |
| Canary | Large changes, gradual rollout | Low |
| Feature Flags | New features, instant rollback | Lowest |

**Blue/Green Deploy:**
```bash
# Deploy to green (inactive)
docker-compose -f docker-compose.green.yml up -d

# Run smoke tests
npm run smoke-test -- --env green

# Switch traffic
# Update load balancer to green

# Monitor
watch docker-compose logs -f
```

**Canary Deploy:**
```bash
# 10% traffic to new version
kubectl set image deployment/myapp app=myapp:2.1.0 --record
kubectl rollout status deployment/myapp

# Monitor error rates
# If healthy → 50%, then 100%
# If issues → kubectl rollout undo
```

---

### Step 4: VERIFY (Post-Deploy)

**Health Checks:**
```bash
# Wait for rollout
kubectl rollout status deployment/myapp

# Check health
curl https://api.example.com/health

# Check metrics
# - Error rate < 0.1%
# - Latency p99 < 500ms
# - CPU < 70%
```

**Smoke Tests:**
```bash
npm run smoke-test -- --env production
```

**Output:**
```
## Deployment Verified

- Health: ✅ / ❌
- Smoke Tests: ✅ / ❌
- Error Rate: N%
- Latency p99: Nms
- Status: Deployed Successfully ✅
```

---

### Step 5: MONITOR & DOCUMENT

**Post-Deploy Monitoring (15-30 min):**
- Error rates stable
- Latency normal
- No increase in 5xx errors
- User reports (if visible changes)

**Post-Deploy Checklist:**
```
## Post-Deploy Complete

- Deployed To: production
- Version: 2.1.0
- Rollback Version: 2.0.9
- Duration: 8m 23s
- Incident: None
```

---

## Rollback Procedures

**When to Rollback:**
- Error rate > 1%
- Latency p99 > 2x normal
- Critical bug discovered
- Security issue introduced

**How to Rollback:**
```bash
# Docker (direct)
docker-compose pull myapp:previous
docker-compose up -d myapp:previous

# Kubernetes
kubectl rollout undo deployment/myapp
kubectl rollout status deployment/myapp
```

---

## CI/CD Pipeline

**Pipeline Stages:**
```yaml
stages:
  - lint:        # Fast, catch style issues
  - test:        # Unit + Integration
  - build:       # Compile, package
  - security:    # Scan for vulnerabilities
  - deploy-staging:  # Automatic on main
  - e2e:         # Full test suite
  - deploy-prod: # Manual approval gate
```

---

## Constraints
- Never skip tests in deploy - If tests failing, find root cause
- Rollback plan first - Can't deploy without knowing how to undo
- Monitor immediately - First 15 min are critical
- Communicate changes - Team should know what's deployed

## Closing
After deploy: "Deployed: version [X.X.X] → [target], Rollback: [how to undo], Monitor: [where to watch]"
