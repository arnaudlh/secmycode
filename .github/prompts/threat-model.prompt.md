---
description: "Create a STRIDE threat model for an application or feature, mapped to CSA Secure Vibe Coding Guide controls"
mode: "ask"
---

# Threat Model

Create a STRIDE threat model for the described system, following **CSA Secure Vibe Coding Guide** principles.

## Analysis Steps

1. **Identify components**: services, APIs, databases, external integrations, user interfaces
2. **Map data flows**: how data moves between components, where trust boundaries exist
3. **Apply STRIDE**: for each component/flow, enumerate Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege threats
4. **Assess risk**: rate each threat by Likelihood (L/M/H) × Impact (L/M/H/C)
5. **Map mitigations**: reference specific CSA §2.x controls and OWASP countermeasures
6. **Generate diagram**: produce a Mermaid data flow diagram showing trust boundaries

## Output

Provide:
- System overview and trust boundaries
- Threat table (ID, Component, STRIDE category, Description, Risk, CSA §, Mitigation)
- Mermaid data flow diagram
- Top 5 prioritized recommendations

## System to Model

#{input:Describe the application, feature, or architecture to threat model}
