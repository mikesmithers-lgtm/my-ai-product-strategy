# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | User corrects something in chat | Updated golden dataset, reviewed by PM | Y | missing |
| Cross-Domain Transfer | None | Nothing has been produced yet | N | missing |
| Network Intelligence | All teams | Shared evals | N | missing |

**Broken loop identified by partner:** None.
**Fix plan:** Route user corrections from chat into golden dataset updates, reviewed by the PM before approval.

## Context Connectivity

Knowledge does not currently flow across teams. Each team keeps its own knowledge, so it silos within each team.

## Governance Policy

**Scope:** The AI objectives assistant, customer-facing. It drafts SMART objectives from 1–3 sentence inputs.

**Autonomy boundaries:**
- OK solo: drafting objectives and showing confidence labels (high, medium, low).
- Needs human: the user must approve the objective wording before it is used.
- Never: store personal data.
- Chat logs are retained for 7 days.
- Deletion requests are handled within 30 days.

**Escalation triggers:**
1. A user flags a response. Flags are reviewed within 1 week.
2. Discriminatory framing is detected.
3. A prompt injection attempt is detected.

**Escalation owner:** Compliance team.
**Audit cadence:** Monthly, owned by the PM.
**Regulatory exposure (EU AI Act / other):** EU AI Act and GDPR. Risk tier: high.

## Agent Topology

Not applicable: single model call.

## Shadow AI Audit

### Internal tools

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| ChatGPT | | M (suggested) | govern (suggested) |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:** 1
**Tools after triage:**
**Estimated hidden spend:**

### Customer workarounds (lab)

Goal: surface at least 5 AI workarounds customers have built around the product. Classify each signal as workflow, trust, capability or pricing gap, then decide: build, partner or ignore.

Signals are hypotheses until confirmed with evidence from support tickets, sales calls or usage data.

| Workaround | Signal | Frequency | Decision |
|------------|--------|-----------|----------|
| Exporting objectives to a spreadsheet or Word doc to reshape them | workflow | monthly | build (suggested) |
| Re-typing drafts into the performance review or HR system | workflow | monthly | partner (suggested) |
| Checking drafts in ChatGPT against SMART criteria | trust | monthly | build (suggested) |
| Running output through a second AI to make it sound more senior | trust / capability | monthly | ignore (suggested) |

**Workarounds:** 4 (pending evidence)
**Build candidates:** Exporting objectives; checking drafts against SMART criteria (suggested)
**Adjacent spend ($/mo):** High
