---
description: "Start a security planning session: scoping, STRIDE threat modeling, standards mapping, and remediation backlog"
mode: "ask"
agent: "security-planner"
---

# Security Plan

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional security tooling or qualified human review. All generated security plans **must** be reviewed by qualified security professionals before use.

Start a security planning session for my project. Guide me through:

1. **Scoping** — Technology stack, deployment targets, data classification, compliance requirements
2. **Operational Bucket Analysis** — Classify components into infrastructure, DevOps, build, messaging, data, web/UI, and identity/auth buckets
3. **Standards Mapping** — Map controls from OWASP Top 10, NIST 800-53, CIS Benchmarks, and CSA Secure Vibe Coding Guide
4. **STRIDE Threat Modeling** — Apply STRIDE per bucket with risk scoring (Likelihood × Impact)
5. **Remediation Backlog** — Generate prioritized work items for each threat and control gap
6. **Review and Handoff** — Summary, completeness validation, and handoff

Ask me 3–5 focused questions per turn to gather the information needed for each phase. Use checklists to track progress. Do not advance to the next phase without my confirmation.

## Project Details

#{input:Describe your project: name, purpose, and any initial context about the technology stack or security concerns}
