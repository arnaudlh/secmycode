---
description: "Comprehensive pre-PR code review checklist covering security, performance, testing, and quality. Inspired by microsoft/skills code-review prompt."
mode: "ask"
---

# Code Review Checklist

Review the following code changes against this comprehensive checklist. For each category, flag any violations found.

## Security
- [ ] No hardcoded secrets, API keys, or credentials in code or comments
- [ ] Authentication required for all write/mutation operations
- [ ] Authorization checks enforce least privilege (RBAC/ABAC)
- [ ] All user input validated and sanitized (no injection vectors)
- [ ] No SQL/NoSQL injection vulnerabilities (parameterized queries used)
- [ ] No XSS vulnerabilities (output encoding, no `dangerouslySetInnerHTML` with user data)
- [ ] No command injection (`exec`, `eval`, `system` with user input)
- [ ] CORS configured with explicit origins (no wildcard `*`)
- [ ] Security headers set (HSTS, X-Content-Type-Options, X-Frame-Options, CSP)
- [ ] Rate limiting applied on sensitive endpoints
- [ ] Sensitive data encrypted in transit (TLS 1.2+) and at rest (AES-256)
- [ ] Error messages don't leak system internals (stack traces, paths, SQL)
- [ ] No `console.log()` or debug statements in production paths
- [ ] Dependencies have no known CVEs (`npm audit`, `pip-audit`)

## Code Quality
- [ ] No `any` types (TypeScript) or untyped variables
- [ ] No commented-out code blocks
- [ ] Clear, descriptive variable and function names
- [ ] Appropriate error handling (try/catch, error boundaries)
- [ ] No hardcoded magic numbers or strings (use constants)
- [ ] DRY — no unnecessary duplication

## Performance
- [ ] No N+1 query patterns
- [ ] Expensive computations memoized or cached
- [ ] API calls not in render/hot paths
- [ ] Database queries use indexes and pagination
- [ ] Large datasets streamed, not loaded fully into memory

## Testing
- [ ] Unit tests for new functions and business logic
- [ ] Integration tests for new API endpoints
- [ ] Edge cases and error scenarios covered
- [ ] Tests pass locally

## Documentation
- [ ] Complex logic has explanatory comments
- [ ] Public APIs have clear signatures and types
- [ ] README updated if needed
- [ ] Breaking changes documented

## Commit Hygiene
- [ ] Follows conventional commit format
- [ ] Commit message describes *why*, not just *what*
- [ ] No unrelated changes bundled
- [ ] Lint and build pass

---

Report findings as: **Category**, **Severity** (Critical/High/Medium/Low), **Location**, **Issue**, **Fix**.

#{file}
