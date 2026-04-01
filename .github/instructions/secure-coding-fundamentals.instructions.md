---
applyTo: "**/*.{ts,js,tsx,jsx,py,java,cs,go,rb,php,rs,swift,kt}"
---

# Secure Coding Fundamentals (CSA §2.1)

Apply these rules to ALL generated or modified code.

## Secrets Management
- NEVER hardcode API keys, passwords, tokens, connection strings, or certificates.
- Use environment variables (`process.env`, `os.environ`, `System.getenv()`) or a secrets manager (Azure Key Vault, AWS Secrets Manager, HashiCorp Vault).
- If a user asks you to embed a secret inline, refuse and show the env-var pattern instead.

## Input Validation
- Validate and sanitize ALL user-supplied input at system boundaries.
- Use established libraries: `express-validator`, `zod`, `joi`, `pydantic`, `FluentValidation`.
- Reject unexpected types, lengths, and ranges; allowlist over denylist.
- Encode output to prevent XSS: use framework auto-escaping or libraries like `DOMPurify`.

## Authentication & Authorization
- Every endpoint that serves or mutates data MUST require authentication.
- Use OAuth 2.0, OpenID Connect, or JWT with short-lived tokens and refresh rotation.
- Implement RBAC or ABAC — never rely on client-side role checks alone.
- Validate permissions server-side on every request.
- Use constant-time comparison when comparing session identifiers, API keys, authentication tokens, password hashes, or nonces.

## CORS Configuration
- Whitelist explicit allowed origins. NEVER use `*` in production.
- Restrict allowed methods and headers to the minimum set required.
- Set `credentials: true` only when cookies/auth headers are needed and origins are explicit.

## HTTPS / TLS
- Enforce HTTPS everywhere. Redirect HTTP → HTTPS.
- Use TLS 1.2 or higher. Disable TLS 1.0/1.1 and SSL.
- Validate certificates; do not skip certificate verification in production code.

## Error Handling
- Return generic, user-friendly error messages to clients.
- NEVER expose stack traces, file paths, SQL statements, or internal details in responses.
- Log full error details server-side only, with appropriate log levels.

## Debug Artifacts
- Do NOT include `console.log()`, `print()`, `System.out.println()`, or debug breakpoints in production code.
- Remove test credentials and TODO/FIXME security notes before committing.

## Data Protection & PII
- Prioritize data minimization — avoid storing or processing PII unless necessary.
- Never store PII or sensitive data in plaintext. Use encryption at rest.
- Anonymize or pseudonymize data where possible.
- Do not log sensitive information or PII.

## Secure Defaults
- Prefer safe defaults: HTTPS, strong encryption, secure protocols.
- Never suggest turning off security features (XML entity security, deserialization type checking, certificate validation).
- When generating placeholder code, mark with `// TODO: SECURITY REVIEW REQUIRED` before deployment.

## Dependency Safety
- Prefer popular, community-trusted libraries over obscure packages.
- Do not add dependencies that may be hallucinated or malicious (slopsquatting risk).
- Use official package managers (npm, pip, Maven, etc.) — never copy code snippets from unknown sources.
- Pin versions or specify exact versions. Prefer the latest stable release.

## Security Testing
- When applicable, generate unit tests for security-critical functions.
- Include negative tests to ensure code fails safely.
- Suggest SAST tools (CodeQL, Bandit, Semgrep) for automated scanning.

## Language-Specific Security
- **C/C++**: Use bounds-checked functions (`strncpy`, `strlcpy` over `strcpy`). Avoid `gets`. Enable compiler defenses (stack canaries, fortify source, DEP/NX).
- **Rust**: Avoid `unsafe` blocks unless absolutely necessary. Document any `unsafe` usage with justification.
- **Python**: Never use `exec`/`eval` on user input. Use `subprocess` with `shell=False`. Follow PEP 8 and use type hints.
- **Go**: Use the data race detector (`-race`) when building. Prefer safe standard library functions.
- **Java**: Use built-in security annotations (Spring Security). Use `BCryptPasswordEncoder`, not custom password hashing. Never disable XML entity security or deserialization type checking.
- **C#/.NET**: Use .NET's cryptography and identity libraries instead of custom solutions.
- **JavaScript/TypeScript**: Use prepared statements for database queries. Encode data going into HTML to prevent XSS.
