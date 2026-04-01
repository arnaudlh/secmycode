---
description: "Run OWASP Top 10 web vulnerability scan focused on web application security. Inspired by microsoft/hve-core."
mode: "ask"
---

# Web Vulnerability Scan

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional security tooling (SAST, DAST, SCA, penetration testing) or qualified human review.

Run an **OWASP Top 10 (2021)** vulnerability assessment focused on web application security.

Scan for:

| OWASP | Category | Key Checks |
|-------|----------|------------|
| A01 | Broken Access Control | Missing auth, IDOR, CORS `*`, path traversal |
| A02 | Cryptographic Failures | Hardcoded secrets, weak hashing, missing TLS |
| A03 | Injection | SQL, XSS, command, NoSQL, LDAP injection |
| A04 | Insecure Design | Missing rate limiting, no input schemas |
| A05 | Security Misconfiguration | Debug mode, default creds, verbose errors, missing headers |
| A06 | Vulnerable Components | CVE dependencies, unpinned versions |
| A07 | Auth Failures | Weak passwords, no brute-force protection |
| A08 | Data Integrity Failures | Insecure deserialization, unsigned pipelines |
| A09 | Logging Failures | Missing audit logs, sensitive data in logs |
| A10 | SSRF | User-controlled URLs in server-side requests |

For each finding report: **OWASP ID**, **Severity**, **File:Line**, **Issue**, and **Fix**.

End with a severity breakdown and prioritized remediation plan.

#{file}
