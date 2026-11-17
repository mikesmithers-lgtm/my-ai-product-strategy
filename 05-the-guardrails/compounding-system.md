# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | User corrects something in chat | Updated golden dataset, reviewed by PM | Y | missing |
| Cross-Domain Transfer | None | Nothing has been produced yet | N | missing |
| Network Intelligence | All teams | Shared evals | N | missing |

**Broken loop identified by partner:**
**Fix plan:**

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

## Governance Policy

**Scope:** The AI objectives assistant, customer-facing. It drafts SMART objectives from 1–3 sentence inputs.
**Autonomy boundaries:**
- OK solo: drafting objectives and showing confidence labels (high, medium, low).
- Needs human: the user must approve the objective wording before it is used.

**Escalation triggers:** A user can flag a response.
**Escalation owner:** Compliance team.
**Audit cadence:** Monthly.
**Regulatory exposure (EU AI Act / other):** EU AI Act and GDPR. Risk tier: high.

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
