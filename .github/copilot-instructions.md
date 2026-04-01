# Secure Coding Standards — CSA Secure Vibe Coding Guide + OpenSSF Best Practices

These instructions apply to ALL code generated or modified in this workspace.
Based on the [CSA Secure Vibe Coding Guide](https://cloudsecurityalliance.org/blog/2025/04/09/secure-vibe-coding-guide) and the [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html).

## Core Security Principles

1. **Never hardcode secrets.** API keys, database passwords, tokens, and other sensitive data must use environment variables or a secrets manager — never inline literals.
2. **Validate all inputs.** Sanitize and validate every user-supplied value for expected format and length. Use parameterized queries for database access. Escape special characters before rendering in HTML.
3. **Apply least privilege.** Grant only the minimum permissions required. Default to deny; explicitly allow. Drop privileges when running as a service.
4. **Encrypt data.** Use HTTPS/TLS 1.2+ for data in transit. Use AES-256 (or equivalent) for data at rest. Never roll custom crypto — prefer high-level libraries.
5. **Handle errors safely.** Return user-friendly messages. Never expose stack traces, internal paths, or system details to end users. Log detailed errors server-side only. Use logging frameworks that can be configured for security.
6. **Remove debug artifacts.** Strip `console.log()`, debug print statements, and test credentials before code leaves development.
7. **Use parameterized queries.** Never concatenate user input into SQL or NoSQL queries. Always use prepared statements or ORM query builders.
8. **Configure CORS restrictively.** Whitelist specific trusted origins. Never use wildcard (`*`) in production.
9. **Authenticate and authorize every endpoint.** Use OAuth 2.0, JWT, or equivalent. Implement token expiration and refresh. Enforce role-based access control. Use constant-time comparison when comparing session identifiers, API keys, authentication tokens, password hashes, or nonces.
10. **Rate-limit and throttle.** Protect APIs and login endpoints against brute-force and DDoS with rate limiting.
11. **Protect sensitive data.** Prioritize data minimization — avoid storing or processing PII unless necessary. Never store PII in plaintext. Anonymize or pseudonymize data where possible. Avoid logging sensitive information or PII.
12. **Prefer safe defaults.** Use HTTPS by default, require strong encryption, disable insecure protocols. Never suggest turning off security features like XML entity security or deserialization type checking.
13. **Use trusted dependencies only.** Prefer popular, community-trusted libraries over obscure packages. Do not add dependencies that may be hallucinated or malicious (slopsquatting risk). Always use official package managers. Pin versions or specify exact versions.
14. **Mark placeholder code.** If generating placeholder or stub code (e.g., `TODO` comments), ensure it is marked for security review before deployment.

## Security Testing

- When applicable, generate unit tests for security-critical functions, including negative tests to ensure code fails safely.
- Include comments or TODOs suggesting security reviews for complex security logic.
- Encourage use of SAST tools (CodeQL, Bandit, Semgrep) and dependency checkers in CI/CD.

## OWASP LLM Top 10 Awareness

When building or integrating LLM-powered features:

- **Prompt Injection (LLM01):** Constrain model behavior, validate outputs, filter inputs/outputs.
- **Sensitive Information Disclosure (LLM02):** Sanitize training data, apply strict access controls.
- **Supply Chain (LLM03):** Vet data sources, scan for vulnerabilities, maintain model inventory.
- **Data & Model Poisoning (LLM04):** Track data origins, validate outputs, sandbox models.
- **Improper Output Handling (LLM05):** Zero-trust approach to LLM output; encode before rendering.
- **Excessive Agency (LLM06):** Minimize extensions, limit permissions, require human approval for high-impact actions.
- **System Prompt Leakage (LLM07):** Never put secrets in system prompts; enforce controls independently.
- **Vector & Embedding Weaknesses (LLM08):** Fine-grained access controls on vector stores.
- **Misinformation (LLM09):** Use RAG with verified sources, encourage human oversight.
- **Unbounded Consumption (LLM10):** Rate-limit inference, set user quotas, monitor resource usage.

## Repository Hygiene

- Never commit `.env` files, private keys, or credentials. Use `.gitignore`.
- Keep dependencies updated. Enable automated vulnerability scanning (e.g., Dependabot).
- Store webhooks and API tokens in GitHub Secrets or equivalent vault.
- Review access permissions regularly; remove stale collaborators.
- Generate Software Bill of Materials (SBOM) using SPDX or CycloneDX tools.

## Standards Compliance

Code suggestions should adhere to:
- **OWASP Top 10** and **OWASP ASVS** requirements
- **SAFECode** secure development practices
- **CWE/SANS Top 25** most dangerous software weaknesses
- When applicable, consider compliance requirements (HIPAA for medical data, PCI-DSS for credit card info, GDPR for EU personal data) — do not generate code that logs or transmits sensitive data in insecure ways.
