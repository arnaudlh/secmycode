# Changelog

All notable changes to this Secure Vibe Coding Library are documented in this file.

## [Unreleased]

### Added — Copilot CLI Marketplace support

**Marketplace**
- `.github/plugin/marketplace.json` — Marketplace manifest registering 4 installable plugins

**Plugins** (in `plugins/` directory)
- `secure-code-gen` — Secure code generator agent + appsec-review, secrets-scanner, database-security-review skills
- `security-review` — Security reviewer + OWASP scanner agents + api-security-review, llm-security-review, owasp-agentic-review, cloud-deploy-security skills
- `security-planning` — Security planner, threat modeler, SSSC planner, RAI planner agents
- `dependency-audit` — Dependency auditor agent

**Installation**
```bash
copilot plugin marketplace add arnaudlh/secmycode
copilot plugin install secure-code-gen@secmycode
```

### Changed
- README updated with CLI marketplace installation instructions and plugin catalog

## [0.3.0] - 2026-04-01

### Changed — OpenSSF Best Practices integration

All changes based on the [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html).

**`copilot-instructions.md` (global instructions)**
- Added constant-time comparison rule for session IDs, API keys, tokens, nonces (OpenSSF §2)
- Added PII/data protection principle: data minimization, no plaintext PII, anonymization (OpenSSF §2)
- Added safe defaults principle: never disable security features (XML entity, deserialization) (OpenSSF §2)
- Added trusted dependency rule: slopsquatting prevention, official package managers, version pinning (OpenSSF §3)
- Added placeholder code security review markers (OpenSSF §6)
- Added security testing section: negative tests, SAST tool integration (OpenSSF §2)
- Added SBOM generation requirement (SPDX/CycloneDX) to repository hygiene (OpenSSF §3)
- Added standards compliance section: OWASP ASVS, SAFECode, CWE/SANS Top 25, HIPAA/PCI-DSS/GDPR (OpenSSF §6)

**`secure-coding-fundamentals.instructions.md`**
- Added constant-time comparison to authentication section (OpenSSF §2)
- Added Data Protection & PII section (OpenSSF §2)
- Added Secure Defaults section with anti-disable-security rule (OpenSSF §2, §5)
- Added Dependency Safety section with slopsquatting warning (OpenSSF §3)
- Added Security Testing section with negative test guidance (OpenSSF §2)
- Added Language-Specific Security section: C/C++ bounds checks, Rust unsafe, Python exec/eval, Go race detector, Java deserialization, C#/.NET crypto, JS/TS XSS (OpenSSF §5)

**`cloud-deployment.instructions.md`**
- Added container image signing (cosign/notation) and Kubernetes admission controllers (OpenSSF §4)
- Added GitHub Actions SHA pinning with version comments (OpenSSF §4)
- Added SBOM generation (SPDX/CycloneDX) and in-toto attestations (OpenSSF §3)
- Added Infrastructure-as-Code security section (OpenSSF §4)
- Added Integrity Verification section for external resources (OpenSSF §3)
- Changed container pinning from "by digest" to "by immutable digest (SHA256)" with explicit `latest` ban (OpenSSF §4)

**`frontend-security.instructions.md`**
- Added Mobile & Desktop App Security section: platform secure storage APIs, no plaintext sensitive data (OpenSSF §4)

**`database-security.instructions.md`**
- Added PII logging warning to monitoring section (OpenSSF §2)

**`@dependency-auditor` agent**
- Added OpenSSF reference to description
- Added slopsquatting detection (hallucinated package names) to supply chain risks (OpenSSF §3)
- Added missing integrity verification check (OpenSSF §3)
- Added SBOM & Attestation recommendations section (OpenSSF §3)

**`@secure-code-gen` agent**
- Added OpenSSF reference to description
- Added constant-time comparison to auth section (OpenSSF §2)
- Added safe defaults rule: never disable security features (OpenSSF §2)
- Added placeholder code security markers (OpenSSF §6)
- Added Dependency Safety section with slopsquatting prevention (OpenSSF §3)
- Added Security Testing section with negative tests (OpenSSF §2)
- Added Language-Specific Rules section: C/C++, Rust, Python, Go, Java, C#/.NET (OpenSSF §5)

### Sources
- [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html)

## [0.2.0] - 2026-04-01

### Added — microsoft/hve-core & microsoft/skills integration

**Agents**
- `@security-planner` — Phase-based security planning with STRIDE, OWASP Top 10, NIST 800-53, CIS Benchmarks mapping, and operational bucket analysis (inspired by microsoft/hve-core Security Planner)
- `@sssc-planner` — Supply chain security assessment against OpenSSF Scorecard, SLSA Build levels, Sigstore signing, SBOM standards, and Best Practices Badge (inspired by microsoft/hve-core SSSC Planner)
- `@rai-planner` — Responsible AI assessment against NIST AI RMF 1.0 and Microsoft RAI Standard v2, with sensitive uses screening and AI-specific threat modeling (inspired by microsoft/hve-core RAI Planner)

**Skills**
- `owasp-agentic-review` — OWASP Agentic Security Top 10 (AG01–AG10) review for AI agent systems covering excessive autonomy, tool call validation, identity spoofing, audit trails, and more (inspired by microsoft/hve-core owasp-agentic skill)

**Prompts**
- `/security-plan` — Start a security planning session with scoping, STRIDE, standards mapping, and remediation backlog
- `/security-review-web` — OWASP Top 10 web vulnerability scan (inspired by microsoft/hve-core)
- `/security-review-llm-agentic` — Combined OWASP LLM Top 10 + OWASP Agentic Security Top 10 scan (inspired by microsoft/hve-core)
- `/supply-chain-security` — Supply chain security assessment against OpenSSF/SLSA/SBOM standards (inspired by microsoft/hve-core)
- `/incident-response` — Incident response workflow: triage, diagnostics, mitigation, root cause analysis (inspired by microsoft/hve-core)
- `/risk-register` — Generate a Probability × Impact risk register with mitigation plans (inspired by microsoft/hve-core)
- `/code-review` — Comprehensive pre-PR code review checklist covering security, quality, performance, testing, and commit hygiene (inspired by microsoft/skills)

**Instructions**
- `security-model.instructions.md` — STRIDE threat modeling rules, risk scoring matrix, threat ID formats, standards cross-references, operational security buckets, and data flow diagram guidance

### Changed

- `@security-reviewer` — Added multi-mode scanning (audit/diff/plan), OWASP Agentic Security Top 10 checks (section 9), SSRF detection, severity definitions table, structured assessment pipeline, and caution notice

### Sources
- [microsoft/hve-core](https://github.com/microsoft/hve-core) — Security Planner, SSSC Planner, RAI Planner, Security Reviewer, owasp-agentic skill, incident-response prompt, risk-register prompt
- [microsoft/skills](https://github.com/microsoft/skills) — Code review prompt patterns

## [0.1.0] - 2026-04-01

### Added — Initial release based on CSA Secure Vibe Coding Guide

**Instructions**
- `copilot-instructions.md` — Global security principles applied to all code (CSA core)
- `secure-coding-fundamentals.instructions.md` — Secrets, input validation, auth, CORS, HTTPS, error handling, debug artifacts (CSA §2.1)
- `api-security.instructions.md` — Transport security, auth, input validation, rate limiting, API gateway, response security (CSA §2.3)
- `database-security.instructions.md` — Parameterized queries, encryption, least privilege, no frontend access, monitoring (CSA §2.5)
- `frontend-security.instructions.md` — XSS prevention, CSP, cookies, CSRF, SRI, debug removal (CSA §2.1, §2.2, §2.7)
- `cloud-deployment.instructions.md` — TLS, firewall, IAM, secrets, containers, CI/CD, logging (CSA §2.7)

**Agents**
- `@security-reviewer` — Comprehensive security code review (CSA §2.1–§2.8)
- `@secure-code-gen` — Security-first code generation (CSA §2.1–§2.6)
- `@threat-modeler` — STRIDE threat modeling (CSA §2.1–§2.7)
- `@owasp-scanner` — OWASP Top 10 & API Security Top 10 scanning (CSA §2.1–§2.3)
- `@dependency-auditor` — Dependency & supply chain audit (CSA §2.4)

**Prompts**
- `/security-review` — Review current file for vulnerabilities
- `/secure-api-endpoint` — Generate a secure API endpoint
- `/secure-database-query` — Generate a secure database query
- `/threat-model` — Create a STRIDE threat model
- `/llm-security-check` — Check LLM code for OWASP LLM Top 10

**Skills**
- `appsec-review` — Application security review (CSA §2.2)
- `api-security-review` — API endpoint security audit (CSA §2.3)
- `database-security-review` — Database access security (CSA §2.5)
- `secrets-scanner` — Hardcoded secrets detection (CSA §2.1, §2.4)
- `llm-security-review` — LLM/AI integration security (CSA §2.6)
- `cloud-deploy-security` — Cloud deployment & infrastructure security (CSA §2.7)

### Sources
- [CSA Secure Vibe Coding Guide](https://cloudsecurityalliance.org/blog/2025/04/09/secure-vibe-coding-guide)
