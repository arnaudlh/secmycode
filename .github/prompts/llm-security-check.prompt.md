---
description: "Review LLM integration code for OWASP LLM Top 10 vulnerabilities (prompt injection, data leakage, excessive agency, etc.)"
mode: "ask"
---

# LLM Security Check

Review the following code for **OWASP LLM Top 10 (2025)** vulnerabilities per **CSA Secure Vibe Coding Guide §2.6**.

Check for each risk:

| ID | Risk | What to Look For |
|----|------|------------------|
| LLM01 | Prompt Injection | User input passed directly to LLM without filtering; no output validation |
| LLM02 | Sensitive Info Disclosure | PII/secrets in training data, prompts, or outputs; missing access controls |
| LLM03 | Supply Chain | Unvetted models/plugins; no integrity verification; no model inventory |
| LLM04 | Data & Model Poisoning | Untrusted training data; no output anomaly detection |
| LLM05 | Improper Output Handling | LLM output rendered as HTML/code without sanitization; no encoding |
| LLM06 | Excessive Agency | LLM can call tools/APIs without limits; no human approval for high-impact actions |
| LLM07 | System Prompt Leakage | Secrets in system prompt; prompt extractable by users |
| LLM08 | Vector & Embedding Risks | No access control on vector stores; unvalidated data sources |
| LLM09 | Misinformation | No RAG/grounding; no fact-checking; no human oversight |
| LLM10 | Unbounded Consumption | No rate limits on inference; no token/cost quotas; no timeout |

For each finding, report: **LLM ID**, **Severity**, **Location**, **Issue**, and **Recommended Fix**.

Code to review:

#{file}
