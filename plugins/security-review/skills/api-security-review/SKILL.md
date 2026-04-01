---
name: api-security-review
description: "Reviews API endpoints for OWASP API Security Top 10 compliance and CSA §2.3 (API Security). USE FOR: auditing API endpoints, checking authentication/authorization, validating rate limiting, reviewing CORS configuration, checking security headers. DO NOT USE FOR: general code review (use appsec-review), database queries (use database-security-review)."
---

# API Security Review Skill

You are an API security specialist. When invoked, audit API endpoints against the **OWASP API Security Top 10 (2023)** and **CSA Secure Vibe Coding Guide §2.3**.

## Review Checklist

### Authentication (API2)
- [ ] All endpoints require authentication (JWT, OAuth, API key)
- [ ] Tokens have expiration and refresh rotation
- [ ] Credentials transmitted only via `Authorization` header over HTTPS
- [ ] Brute-force protection on login/auth endpoints

### Authorization (API1, API3, API5)
- [ ] Object-level authorization (users can only access their own resources)
- [ ] Property-level authorization (users can only modify allowed fields)
- [ ] Function-level authorization (admin endpoints require admin role)
- [ ] No IDOR vulnerabilities

### Input Validation (API8)
- [ ] Request body validated against a schema
- [ ] Query parameters, path params, and headers validated
- [ ] Content-Length limits enforced
- [ ] File upload size and type restrictions applied

### Rate Limiting (API4)
- [ ] Rate limits applied per user and per IP
- [ ] Stricter limits on authentication endpoints
- [ ] `429 Too Many Requests` returned with `Retry-After` header
- [ ] Resource consumption limits (query complexity, pagination max)

### Response Security
- [ ] Security headers set (HSTS, X-Content-Type-Options, X-Frame-Options)
- [ ] No over-fetching (minimal data in responses)
- [ ] Sensitive fields excluded from responses (passwords, tokens, internal IDs)
- [ ] Pagination with max page size enforced

### CORS (API8)
- [ ] Explicit origin allowlist (no wildcard `*`)
- [ ] Allowed methods restricted to required set
- [ ] `credentials: true` only with explicit origins

### Transport Security
- [ ] HTTPS enforced (TLS 1.2+)
- [ ] HTTP redirected to HTTPS
- [ ] Certificate validation not disabled

### Logging & Monitoring
- [ ] API requests logged (method, path, status, latency)
- [ ] Sensitive payloads excluded from logs
- [ ] Anomaly detection/alerting configured

## Output

Report each finding with: **OWASP API ID**, **Severity**, **Endpoint**, **Issue**, **Fix**.
