---
description: "Assess supply chain security posture against OpenSSF Scorecard, SLSA, Sigstore, and SBOM standards. Inspired by microsoft/hve-core SSSC Planner."
mode: "ask"
agent: "sssc-planner"
---

# Supply Chain Security Assessment

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional supply chain security tooling (OpenSSF Scorecard, SLSA verification, Sigstore, SBOM validators) or qualified human review.

Assess this repository's software supply chain security posture. Guide me through:

1. **Scoping** — Technology stack, package managers, CI/CD platform, release strategy
2. **Supply Chain Assessment** — Evaluate dependency management, build integrity, source integrity, artifact security, CI/CD security, release management
3. **Standards Mapping** — Map against OpenSSF Scorecard (20 checks), SLSA Build levels (L0–L3), Sigstore, SBOM standards (CycloneDX/SPDX), Best Practices Badge
4. **Gap Analysis** — Current vs. target maturity with effort estimates
5. **Remediation Backlog** — Prioritized work items with adoption steps
6. **Projections** — Estimated Scorecard improvement, achievable SLSA level, Badge tier

Ask 3–5 questions per turn. Use checklists to track progress. Do not advance without my confirmation.

## Project Details

#{input:Describe your project and any existing supply chain security measures (Dependabot, CodeQL, signed commits, etc.)}
