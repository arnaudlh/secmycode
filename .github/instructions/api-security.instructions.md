---
applyTo: "**/{routes,api,controllers,endpoints,handlers,middleware}/**/*.{ts,js,py,java,cs,go,rb,php}"
---

# API Security Rules (CSA §2.3 — OWASP API Security Top 10)

Apply these rules when generating or modifying API endpoints.

## Transport Security
- ALL API communication MUST use HTTPS with TLS 1.2+.
- Never transmit tokens, credentials, or PII over unencrypted channels.

## Authentication & Authorization
- Every API endpoint MUST require authentication (OAuth 2.0, JWT, API key).
- Implement token expiration (short-lived access tokens) and secure refresh flows.
- Validate scopes and roles server-side before processing the request.
- Use `Authorization` header (Bearer tokens), not query parameters, for credentials.

## Input Validation
- Validate request body, query parameters, path parameters, and headers.
- Reject payloads exceeding expected size limits (set `Content-Length` limits).
- Use schema validation (OpenAPI spec, JSON Schema, zod) to enforce structure.
- Sanitize inputs to prevent SQL injection, NoSQL injection, and command injection.

## Rate Limiting & Throttling
- Apply rate limits per IP and per authenticated user on all endpoints.
- Use progressive back-off for repeated failed authentication attempts.
- Return `429 Too Many Requests` with `Retry-After` header.
- Implement stricter limits on login, registration, and password reset endpoints.

## API Gateway Best Practices
- Use an API gateway for centralized logging, monitoring, auth, and rate limiting.
- Do not expose internal service endpoints directly to the public internet.
- Log all API requests (method, path, status, latency) without logging sensitive payloads.

## Response Security
- Set security headers: `X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY`, `Strict-Transport-Security`.
- Never return more data than the client needs (avoid over-fetching / mass assignment).
- Use pagination for list endpoints; set maximum page sizes.
- Mask or exclude sensitive fields (passwords, tokens, SSN) from all responses.

## Versioning & Deprecation
- Version APIs explicitly (URL path or header).
- Document breaking changes and deprecation timelines.
