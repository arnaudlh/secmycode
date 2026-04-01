---
description: "Run a security review on the current file or selection against the CSA Secure Vibe Coding Guide checklist"
mode: "ask"
---

# Security Review

Perform a comprehensive security review of the following code against the **CSA Secure Vibe Coding Guide** checklist.

Check for:
1. **Hardcoded secrets** — API keys, passwords, tokens, connection strings (CSA §2.1)
2. **Input validation gaps** — Missing sanitization, injection vectors (SQL, XSS, command) (CSA §2.1)
3. **Auth & access control** — Unauthenticated endpoints, missing authorization, IDOR (CSA §2.1, §2.3)
4. **CORS misconfiguration** — Wildcard origins, overly permissive settings (CSA §2.1)
5. **Cryptographic issues** — Weak algorithms, missing encryption, custom crypto (CSA §2.2)
6. **Error handling** — Exposed stack traces, verbose errors to users (CSA §2.2)
7. **Database security** — SQL concatenation, excessive privileges (CSA §2.5)
8. **API security** — Missing rate limiting, over-fetching, missing headers (CSA §2.3)
9. **Debug artifacts** — `console.log()`, test credentials, TODO security notes (CSA §2.2)
10. **LLM risks** — Prompt injection, unsanitized outputs, excessive agency (CSA §2.6)

For each finding, report: **Severity** (Critical/High/Medium/Low), **Location**, **Issue**, and **Fix**.

Code to review:

#{file}
