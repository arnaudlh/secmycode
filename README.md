# Secure my Code: A Copilot Agent Library for Secure Coding

A library of GitHub Copilot agents, instructions, skills, and prompts for secure coding, based on the [Cloud Security Alliance Secure Vibe Coding Guide](https://cloudsecurityalliance.org/blog/2025/04/09/secure-vibe-coding-guide), the [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html), with additional patterns from [microsoft/hve-core](https://github.com/microsoft/hve-core) and [microsoft/skills](https://github.com/microsoft/skills).

## What's Included

### Instructions (always-on rules)

| File | Scope | Source |
|------|-------|--------|
| [copilot-instructions.md](.github/copilot-instructions.md) | All code in workspace | CSA Core principles |
| [secure-coding-fundamentals](.github/instructions/secure-coding-fundamentals.instructions.md) | `*.ts, *.js, *.py, *.java, *.cs, *.go` ... | CSA §2.1 |
| [api-security](.github/instructions/api-security.instructions.md) | `routes/`, `api/`, `controllers/` ... | CSA §2.3 |
| [database-security](.github/instructions/database-security.instructions.md) | `models/`, `db/`, `migrations/` ... | CSA §2.5 |
| [frontend-security](.github/instructions/frontend-security.instructions.md) | `*.html, *.jsx, *.tsx, *.vue, *.svelte` | CSA §2.1, §2.2, §2.7 |
| [cloud-deployment](.github/instructions/cloud-deployment.instructions.md) | `infra/`, `docker/`, `*.tf, *.bicep` ... | CSA §2.7 |
| [security-model](.github/instructions/security-model.instructions.md) | `security/`, `threat-model/` ... | STRIDE + NIST + hve-core |

> Instructions activate automatically based on `applyTo` glob patterns — no manual invocation needed.

### Agents (invoke with `@agent-name`)

| Agent | Purpose | Source |
|-------|---------|--------|
| `@security-reviewer` | Multi-mode OWASP vulnerability assessment (audit/diff/plan) | CSA + hve-core |
| `@secure-code-gen` | Security-first code generation | CSA §2.1–§2.6 |
| `@threat-modeler` | STRIDE threat modeling | CSA §2.1–§2.7 |
| `@owasp-scanner` | OWASP Top 10 & API Top 10 scanning | CSA §2.1–§2.3 |
| `@dependency-auditor` | Dependency & supply chain audit | CSA §2.4 |
| `@security-planner` | Phase-based security planning (STRIDE, NIST, CIS) | hve-core |
| `@sssc-planner` | Supply chain security assessment (OpenSSF, SLSA, SBOM) | hve-core |
| `@rai-planner` | Responsible AI assessment (NIST AI RMF, Microsoft RAI) | hve-core |

### Prompts (invoke with `/prompt-name`)

| Prompt | Purpose | Source |
|--------|---------|--------|
| `/security-review` | Review current file for vulnerabilities | CSA §2.1–§2.6 |
| `/secure-api-endpoint` | Generate a secure API endpoint | CSA §2.3 |
| `/secure-database-query` | Generate a secure database query | CSA §2.5 |
| `/threat-model` | Create a STRIDE threat model | CSA §2.1–§2.7 |
| `/llm-security-check` | Check LLM code for OWASP LLM Top 10 | CSA §2.6 |
| `/security-review-web` | OWASP Top 10 web vulnerability scan | hve-core |
| `/security-review-llm-agentic` | Combined OWASP LLM + Agentic scan | hve-core |
| `/security-plan` | Start a security planning session | hve-core |
| `/supply-chain-security` | Supply chain security assessment | hve-core |
| `/incident-response` | Incident response workflow (triage → RCA) | hve-core |
| `/risk-register` | Generate a P×I risk register | hve-core |
| `/code-review` | Pre-PR code review checklist | ms/skills |

### Skills (referenced by agents)

| Skill | Domain | Source |
|-------|--------|--------|
| `appsec-review` | Application security review | CSA §2.2 |
| `api-security-review` | API endpoint security audit | CSA §2.3 |
| `database-security-review` | Database access security | CSA §2.5 |
| `secrets-scanner` | Hardcoded secrets detection | CSA §2.1, §2.4 |
| `llm-security-review` | LLM/AI integration security | CSA §2.6 |
| `cloud-deploy-security` | Cloud deployment & infra security | CSA §2.7 |
| `owasp-agentic-review` | AI agent system security | hve-core |

## Coverage Map

| Domain | Instructions | Agents | Skills | Prompts |
|--------|-------------|--------|--------|---------|
| **Secure Coding Fundamentals** | `copilot-instructions`, `secure-coding-fundamentals` | `security-reviewer`, `secure-code-gen` | `secrets-scanner` | `/security-review`, `/code-review` |
| **Application Security** | `secure-coding-fundamentals` | `security-reviewer`, `secure-code-gen` | `appsec-review` | `/security-review` |
| **API Security** | `api-security` | `security-reviewer`, `owasp-scanner` | `api-security-review` | `/secure-api-endpoint`, `/security-review-web` |
| **Repository & Supply Chain** | `copilot-instructions` | `dependency-auditor`, `sssc-planner` | `secrets-scanner` | `/supply-chain-security` |
| **Database Security** | `database-security` | `security-reviewer` | `database-security-review` | `/secure-database-query` |
| **LLM Security** | `copilot-instructions` | `security-reviewer`, `secure-code-gen` | `llm-security-review` | `/llm-security-check`, `/security-review-llm-agentic` |
| **Agentic Security** | `copilot-instructions` | `security-reviewer` | `owasp-agentic-review` | `/security-review-llm-agentic` |
| **Cloud Deployment** | `cloud-deployment` | `security-reviewer` | `cloud-deploy-security` | — |
| **Threat Modeling & Planning** | `security-model` | `threat-modeler`, `security-planner` | — | `/threat-model`, `/security-plan` |
| **Responsible AI** | — | `rai-planner` | — | — |
| **Risk Management** | — | `security-planner` | — | `/risk-register`, `/incident-response` |

## Quick Start

1. **Clone this repo** into your project or copy the `.github/` folder.
2. **Instructions activate automatically** based on file patterns when you use Copilot.
3. **Use agents** by typing `@security-reviewer`, `@security-planner`, etc. in Copilot Chat.
4. **Use prompts** by typing `/security-review`, `/security-plan`, etc. in Copilot Chat.

## Usage Examples

```
# Full codebase security audit
@security-reviewer Run an audit of this codebase

# Review only changed files (diff mode)
@security-reviewer Scan my changes in diff mode

# Generate a secure REST endpoint
/secure-api-endpoint POST /api/users - create a new user with email and password

# Start security planning
/security-plan My new e-commerce application using Node.js, PostgreSQL, and React

# Create a threat model
@threat-modeler Model threats for our e-commerce checkout flow

# Audit dependencies and supply chain
@dependency-auditor Scan this project for vulnerable dependencies
/supply-chain-security We use GitHub Actions, npm, and Dependabot

# Check LLM + agent integration
/security-review-llm-agentic

# OWASP Top 10 web scan
/security-review-web

# Responsible AI assessment
@rai-planner Assess our recommendation engine for RAI risks

# Incident response
/incident-response Production API returning 500 errors since 2pm, user auth service affected

# Risk register
/risk-register Cloud migration project using Azure Kubernetes Service

# Pre-PR code review
/code-review
```

## Sources & References

- [CSA Secure Vibe Coding Guide](https://cloudsecurityalliance.org/blog/2025/04/09/secure-vibe-coding-guide) — Core security checklist and principles
- [OpenSSF Security-Focused Guide for AI Code Assistant Instructions](https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html) — Constant-time comparison, language-specific rules, supply chain safety, SBOM, PII protection
- [microsoft/hve-core](https://github.com/microsoft/hve-core) — Security Planner, SSSC Planner, RAI Planner, Security Reviewer patterns
- [microsoft/skills](https://github.com/microsoft/skills) — Code review prompt, agent patterns
- [OWASP Top 10 (2021)](https://owasp.org/www-project-top-ten/)
- [OWASP API Security Top 10 (2023)](https://owasp.org/API-Security/)
- [OWASP LLM Top 10 (2025)](https://genai.owasp.org/)
- [OWASP Agentic Security Top 10](https://owasp.org/www-project-agentic-security/)
- [OWASP Secure Coding Practices](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)
- [NIST SP 800-53](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
- [NIST AI RMF 1.0](https://www.nist.gov/artificial-intelligence/ai-risk-management-framework)
- [OpenSSF Scorecard](https://scorecard.dev/)
- [SLSA Framework](https://slsa.dev/)
