---
description: "Guide incident response for security events: triage, diagnostics, mitigation, and root cause analysis. Inspired by microsoft/hve-core."
mode: "ask"
---

# Incident Response

> [!CAUTION]
> This prompt is an **assistive tool only** and does not replace professional incident management platforms, security tooling, or qualified human review. All generated triage assessments, mitigation recommendations, and RCA documentation **must** be reviewed by qualified professionals before use.

Guide me through structured incident response for a security event.

## Phase 1: Initial Triage
- **What is happening?** Symptoms, error messages, user reports
- **When did it start?** Timeline and first detection
- **What is affected?** Services, resources, regions, user segments
- **What changed recently?** Deployments, configuration changes, scaling events
- Severity assessment (1=Critical, 2=High, 3=Medium, 4=Low)
- Confirm incident is genuine (not a false positive)

## Phase 2: Diagnostic Investigation
- Identify relevant data sources (logs, metrics, traces)
- Build targeted queries for the incident timeframe
- Key diagnostic areas: resource health, error analysis, change detection, performance, dependency health
- Review application logs, infrastructure logs, and audit trails

## Phase 3: Mitigation Actions
- Assess risk of each potential mitigation
- Document rollback plan before applying changes
- Identify verification steps (how to confirm the fix worked)
- Communication templates for internal and customer updates

## Phase 4: Root Cause Analysis (RCA)
Use the Five Whys method:
1. **Why** did the service fail? →
2. **Why** did that happen? →
3. **Why** was that the case? →
4. **Why** wasn't this prevented? →
5. **Why** wasn't this detected earlier? →

Document: timeline, root cause, contributing factors, impact, remediation actions, and prevention measures.

## Incident Details

#{input:Describe the incident: symptoms, affected services, when it started, and any recent changes}
