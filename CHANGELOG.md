# Changelog

All notable changes to this Secure Vibe Coding Library are documented in this file.

## [0.0.1] - 2026-04-01

Initial release of the Secure Vibe Coding Library — a collection of GitHub Copilot agents, instructions, skills, prompts, and CLI plugins for secure coding.

### Sources

- [CSA Secure Vibe Coding Guide](https://cloudsecurityalliance.org/blog/2025/04/09/secure-vibe-coding-guide)
- [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html)
- [microsoft/hve-core](https://github.com/microsoft/hve-core)
- [microsoft/skills](https://github.com/microsoft/skills)

### Copilot CLI Marketplace

- `.github/plugin/marketplace.json` — Marketplace manifest with 4 installable plugins
- `secure-code-gen` — Secure code generator agent + appsec-review, secrets-scanner, database-security-review skills
- `security-review` — Security reviewer + OWASP scanner agents + API, LLM, agentic, cloud deploy skills
- `security-planning` — Security planner, threat modeler, SSSC planner, RAI planner agents
- `dependency-audit` — Dependency auditor agent

### Instructions

- `copilot-instructions.md` — Global security principles (CSA + OpenSSF): secrets, input validation, least privilege, encryption, error handling, CORS, auth, rate limiting, PII protection, safe defaults, dependency safety, SBOM, standards compliance (OWASP ASVS, SAFECode, CWE/SANS Top 25, HIPAA/PCI-DSS/GDPR)
- `secure-coding-fundamentals.instructions.md` — Secrets, input validation, auth with constant-time comparison, CORS, HTTPS, error handling, debug artifacts, PII protection, secure defaults, dependency safety, security testing, language-specific rules (C/C++, Rust, Python, Go, Java, C#, JS/TS)
- `api-security.instructions.md` — Transport security, auth, input validation, rate limiting, API gateway, response security, CORS
- `database-security.instructions.md` — Parameterized queries, encryption, least privilege, no frontend access, monitoring with PII logging protection
- `frontend-security.instructions.md` — XSS prevention, CSP, cookies, CSRF, SRI, debug removal, mobile/desktop secure storage
- `cloud-deployment.instructions.md` — TLS, firewall, IAM, secrets, container security with image signing (cosign/notation), CI/CD with SHA pinning, SBOM generation, in-toto attestations, IaC security, integrity verification
- `security-model.instructions.md` — STRIDE threat modeling, risk scoring matrix, threat ID formats, standards cross-references, operational security buckets

### Agents

- `@security-reviewer` — Multi-mode OWASP vulnerability assessment (audit/diff/plan) with OWASP Top 10, API Top 10, LLM Top 10, and Agentic Top 10 checks
- `@secure-code-gen` — Security-first code generation with OpenSSF language-specific rules, dependency safety, security testing, and placeholder markers
- `@threat-modeler` — STRIDE threat modeling mapped to CSA controls
- `@owasp-scanner` — OWASP Top 10 & API Security Top 10 automated detection
- `@dependency-auditor` — Dependency & supply chain audit with slopsquatting detection, SBOM recommendations, and integrity verification
- `@security-planner` — Phase-based security planning (STRIDE, NIST 800-53, CIS, operational buckets)
- `@sssc-planner` — Supply chain security assessment (OpenSSF Scorecard, SLSA, Sigstore, SBOM)
- `@rai-planner` — Responsible AI assessment (NIST AI RMF 1.0, Microsoft RAI Standard v2)

### Prompts

- `/security-review` — Review current file for vulnerabilities
- `/secure-api-endpoint` — Generate a secure API endpoint
- `/secure-database-query` — Generate a secure database query
- `/threat-model` — Create a STRIDE threat model
- `/llm-security-check` — Check LLM code for OWASP LLM Top 10
- `/security-review-web` — OWASP Top 10 web vulnerability scan
- `/security-review-llm-agentic` — Combined OWASP LLM + Agentic scan
- `/security-plan` — Start a security planning session
- `/supply-chain-security` — Supply chain security assessment
- `/incident-response` — Incident response workflow (triage → RCA)
- `/risk-register` — Probability × Impact risk register
- `/code-review` — Comprehensive pre-PR code review checklist

### Skills

- `appsec-review` — Application security review (CSA §2.2)
- `api-security-review` — API endpoint security audit (CSA §2.3)
- `database-security-review` — Database access security (CSA §2.5)
- `secrets-scanner` — Hardcoded secrets detection (CSA §2.1, §2.4)
- `llm-security-review` — LLM/AI integration security (CSA §2.6)
- `cloud-deploy-security` — Cloud deployment & infrastructure security (CSA §2.7)
- `owasp-agentic-review` — AI agent system security (OWASP Agentic Top 10)
