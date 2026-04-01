---
description: "Run combined OWASP LLM Top 10 and OWASP Agentic Security Top 10 scan for AI/LLM code. Inspired by microsoft/hve-core."
mode: "ask"
---

# LLM & Agentic Vulnerability Scan

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional security tooling or qualified human review.

Run a combined **OWASP LLM Top 10 (2025)** and **OWASP Agentic Security Top 10** vulnerability assessment on the following code.

## OWASP LLM Top 10

| ID | Risk | Key Checks |
|----|------|------------|
| LLM01 | Prompt Injection | User input in system prompts, missing I/O filtering |
| LLM02 | Sensitive Info Disclosure | PII/secrets in prompts or outputs, missing access controls |
| LLM03 | Supply Chain | Unvetted models/plugins, no integrity checks |
| LLM04 | Data & Model Poisoning | Untrusted training data, no output validation |
| LLM05 | Improper Output Handling | LLM output as HTML/code without sanitization |
| LLM06 | Excessive Agency | Unlimited tool access, no human approval gates |
| LLM07 | System Prompt Leakage | Secrets in system prompts, extractable prompts |
| LLM08 | Vector & Embedding Risks | No access control on vector stores |
| LLM09 | Misinformation | No RAG/grounding, no fact-checking |
| LLM10 | Unbounded Consumption | No rate limits, no token quotas, no timeouts |

## OWASP Agentic Security Top 10

| ID | Risk | Key Checks |
|----|------|------------|
| AG01 | Excessive Autonomy | No human-in-the-loop, unbounded decisions |
| AG02 | Unvalidated Tool Calls | Tool inputs not validated, dangerous tools ungated |
| AG03 | Identity Spoofing | No agent authentication in multi-agent systems |
| AG04 | Missing Audit Trail | Agent actions not logged |
| AG05 | Privilege Escalation | Chained tool calls escalate permissions |
| AG06 | Insecure Communication | Unencrypted or unsigned agent messages |
| AG07 | Resource Consumption | No per-agent quotas, infinite loops |
| AG08 | Error Handling | Failures expose internals or leave insecure state |
| AG09 | Unsafe Output Propagation | Agent output executed as code, cross-agent injection |
| AG10 | Insufficient Monitoring | No anomaly detection, no real-time alerts |

For each finding: **ID**, **Severity**, **Location**, **Issue**, **Fix**.

#{file}
