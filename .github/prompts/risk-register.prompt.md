---
description: "Generate a structured risk register with Probability × Impact matrix, risk scoring, and mitigation plans. Inspired by microsoft/hve-core."
mode: "edit"
---

# Risk Register

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional risk management tooling or qualified human review. All generated risk registers and mitigation strategies **must** be reviewed by qualified professionals before use.

Generate a risk register for the described project using a qualitative **Probability × Impact (P×I)** risk matrix.

## Step 1: Gather Context
Identify: project name, timeline, stakeholders, technical components, known concerns, and sources of uncertainty.

## Step 2: Risk Assessment Methodology
- **Probability**: Low (unlikely), Medium (possible), High (likely)
- **Impact**: Low (minor), Medium (moderate), High (major)
- **Risk Score** = Probability × Impact (H×H=9, H×M=6, M×M=4, L×L=1)
- Document rationale for each rating

## Step 3: Create Risk Register Table

| Risk ID | Risk Title | Description (Cause → Event → Impact) | Probability | Impact | Risk Score | Category | Mitigation | Owner |
|---------|-----------|---------------------------------------|-------------|--------|------------|----------|------------|-------|

Categories: Technical, Security, Operational, Compliance, External, People

## Step 4: Mitigation Plan
For each high-priority risk (score ≥ 6):
- Risk response actions
- Resource requirements
- Trigger events
- Contingency plan
- Reassessment schedule

Sort all risks by descending risk score. Include both technical and non-technical risks.

## Project Details

#{input:Describe your project: name, purpose, technology stack, deployment targets, and any known risks or concerns}
