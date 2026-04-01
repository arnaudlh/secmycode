---
description: "Generate a secure API endpoint with authentication, input validation, rate limiting, and proper error handling"
mode: "edit"
---

# Generate Secure API Endpoint

Generate a secure API endpoint following **CSA Secure Vibe Coding Guide §2.3** (API Security) with these mandatory security controls:

1. **Authentication**: Require a valid JWT/OAuth token. Reject unauthenticated requests with `401`.
2. **Authorization**: Check user roles/permissions before processing. Return `403` for unauthorized access.
3. **Input Validation**: Validate all request parameters using a schema validator (zod, joi, pydantic). Return `400` for invalid input with a generic message.
4. **Rate Limiting**: Apply per-user and per-IP rate limits. Return `429 Too Many Requests` with `Retry-After` header.
5. **Security Headers**: Set `X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY`, `Strict-Transport-Security`.
6. **Error Handling**: Catch all errors. Return user-friendly messages. Log full details server-side only.
7. **Response Filtering**: Return only necessary fields. Never expose passwords, tokens, or internal IDs.
8. **CORS**: Configure explicit origin allowlist (no wildcards).
9. **Parameterized Queries**: If hitting a database, use parameterized queries or ORM — never string concatenation.
10. **No Debug Code**: No `console.log()` or debug statements.

## Endpoint Requirements

#{input:Describe the API endpoint you need (method, path, purpose, data)}
