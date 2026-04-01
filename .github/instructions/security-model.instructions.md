---
applyTo: "**/{security,threat-model,security-plan}/**/*.{md,yaml,yml,json}"
---

# Security Model & Threat Analysis Rules (CSA §2.1–2.7, STRIDE)

Apply these rules when generating or reviewing security models, threat analyses, and risk assessments.

## STRIDE Threat Modeling

Apply STRIDE to every component, data flow, and trust boundary:

| Category | Threat | Typical Mitigations |
|----------|--------|---------------------|
| **Spoofing** | Identity impersonation | Authentication (OAuth, JWT, mTLS), MFA |
| **Tampering** | Data modification in transit/at rest | TLS, message signing, integrity checks, HMAC |
| **Repudiation** | Denial of actions | Audit logging, non-repudiation, signed transactions |
| **Information Disclosure** | Data exposure | Encryption (AES-256, TLS 1.2+), access controls, data masking |
| **Denial of Service** | Availability attacks | Rate limiting, DDoS protection, circuit breakers, auto-scaling |
| **Elevation of Privilege** | Unauthorized access escalation | Least privilege, RBAC, input validation, sandboxing |

## Risk Scoring Matrix

| | Low Impact | Medium Impact | High Impact |
|---|---|---|---|
| **High Likelihood** | Medium | High | Critical |
| **Medium Likelihood** | Low | Medium | High |
| **Low Likelihood** | Low | Low | Medium |

## Threat ID Format
- Use `T-{BUCKET}-{NNN}` for infrastructure threats (e.g., `T-INFRA-001`)
- Use `RAI-T-{CATEGORY}-{NNN}` for AI-specific threats (e.g., `RAI-T-INJECTION-001`)

## Standards Cross-References
Map every identified threat to at least one control from:
- **OWASP Top 10 (2021)** — A01–A10
- **OWASP API Security Top 10 (2023)** — API1–API10
- **OWASP LLM Top 10 (2025)** — LLM01–LLM10 (when AI components present)
- **OWASP Agentic Top 10** — AG01–AG10 (when agent systems present)
- **NIST SP 800-53** — Security and privacy controls
- **CIS Controls v8** — Critical security controls
- **CSA Secure Vibe Coding Guide** — §2.1–§2.7

## Data Flow Diagrams
- Identify all trust boundaries (network, process, machine, user/admin)
- Mark external entities, processes, data stores, and data flows
- Use Mermaid syntax for diagram generation
- Annotate each flow with authentication, encryption, and authorization requirements

## Operational Security Buckets
Classify all components into one of seven operational buckets:
1. Infrastructure (networking, compute, storage)
2. DevOps/Platform-Ops (CI/CD, IaC, deployment)
3. Build (compilation, packaging, artifacts)
4. Messaging (queues, events, webhooks)
5. Data (databases, caches, object stores)
6. Web/UI/Reporting (frontends, APIs, dashboards)
7. Identity/Auth (authentication, authorization, SSO)

Governance & Security (GS) is a cross-cutting overlay applied to all buckets.
