# Cost Curve & Pricing Strategy

*Illustrative figures prepared for a course exercise. All numbers are assumptions, not validated against real usage data.*

## Feature Set

| Feature | Bucket | Description |
|---------|--------|-------------|
| Goal/objective setting | Leader | Rewrites and structures goals and objectives. Highest usage, so it drives most inference volume. |
| Calibration support | Killer | Flags score outliers and suggests consistency checks before calibration sessions. Lowest usage, main differentiator. |
| Feedback-tone checker | Filler | Flags vague, harsh or biased written feedback before submission. Occasional use, low cost. |

## Cost Model

**Assumptions**
- Average call: about 3,000 input tokens and 500 output tokens.
- Frontier model: $3 per million input tokens, $15 per million output tokens (about $0.0165 per call).
- Triage model: $0.25 per million input tokens, $1.25 per million output tokens (about $0.0014 per call).
- 80% of calls are fully handled by triage. 20% escalate to the frontier model.
- Average usage: 23.5 calls per user per month (goal setting 20, calibration 1.5, tone checker 2).

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $0.08 | 20% of calls (about 4.7 per user) escalated to the frontier model |
| Inference (cascading/triage) | $0.03 | Triage model runs on all calls |
| Infrastructure | $0.05 | Hosting and orchestration allowance |
| Data/storage | $0.02 | Stored summaries and audit logs |
| Human-in-the-loop | $0.05 | Allowance for reviewing flagged calibration outputs |
| **Total AI COGS** | **$0.23** | |

Without the cascade, where every call goes to the frontier model, inference alone would be about $0.39 per user per month. The 80/20 split saves roughly $0.31 per user per month on inference.

## Cascading Strategy

**Triage model:** A low-cost, fast model such as Claude Haiku. It reads every incoming call and handles simple, well-defined requests.

**Frontier model:** A higher-capability model such as Claude Sonnet, used only when the task needs deeper reasoning.

**Routing rule:** Route to the frontier model when the triage model reports low confidence, when the input exceeds a set length threshold, or when the output involves calibration judgements that affect ratings. Everything else stays on triage.

**Expected cascade ratio:** 20% of calls escalate to the frontier model, and 80% are fully handled by triage.

## Pricing Model

**Current pricing:** Placeholder seat price of £4 per user per month for the Perform platform, with no AI-specific charge.

**Proposed AI pricing:**
- **Seat fee:** £4 per user per month, covering the platform and the killer feature.
- **Included allowance:** 25 AI actions per user per month.
- **Rollover:** Unused actions carry forward, capped at 50. Rolled-over actions expire after 12 months.
- **Overage:** £0.05 per action beyond the available balance.

**Model:** Hybrid (seat-based base with usage allowance, rollover and overage).

**Monthly usage profile (illustrative, averages 23.5):**

| Month | Calls per user | Notes |
|-------|----------------|-------|
| January | 120 | Start-of-year goal setting surge |
| July | 62 | Mid-year check-in |
| Other 10 months | 10 each | Light, steady use |

## Stress Tests

Infrastructure, data and human review (about $0.12 combined) are held constant in each case.

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | AI COGS rises from $0.23 to about $0.45 (about £0.35), roughly 9% of the £4 seat fee. Gross margin on AI cost stays around 91%. | Absorbed by the seat fee. If sustained, tighten the allowance or lower the escalation rate. |
| Heaviest segment doubles (about 50 calls a month) | With 25 included and 50 banked, 25 calls are overage, adding £1.25. Revenue about £5.25. COGS about £0.28. Margin above 90%. | Consider a higher overage rate or a higher tier if this segment grows. |
| Model provider raises prices 50% | Inference rises from about $0.11 to $0.165. Total AI COGS about $0.29 (about £0.22), roughly 5.5% of the seat fee. | Negotiate volume pricing or move more traffic to triage. Review the routing rule. |
| Escalation rate rises from 20% to 30% | Frontier spend rises, lifting AI COGS from $0.23 to about $0.27. Small margin impact. | Monitor the escalation rate and tune the routing threshold to keep it near 20%. |
| Peak month: goal setting surge (January, 120 calls) | 75 available (25 plus 50 banked), so 45 calls are overage. Overage adds £2.25, revenue £6.25. COGS about £0.54, margin around 91%. | Overage is profitable, but the January bill is the main friction risk. Monitor cap usage. Consider a seasonal allowance or in-app warnings before overage. |

## Board One-Pager

**Before (traditional SaaS):** £4 per user per month, flat seat fee for the Perform platform. Revenue is predictable, but AI features carry no direct cost recovery. AI COGS of about $0.23 (roughly £0.18) per user is absorbed in the seat price.

**After (AI-enabled hybrid):** £4 per user per month seat fee, with 25 AI actions included, a rollover capped at 50, and £0.05 per action beyond the available balance. Average usage of 23.5 calls stays inside the allowance, so most customers pay the seat fee alone. Expected overage comes mainly from January's goal-setting surge, adding about £2.25 for a heavy user that month.

**Net margin shift:** Average AI COGS is about £0.18 per user per month, around 4.5% of the seat fee, leaving a gross margin of about 95% on the AI component. Overage adds upside in peak months, and the rollover limits how much of that upside comes from customer friction rather than real extra usage.

**Key risks:** Inference cost increases, escalation rates above 20%, and January overage driving complaints. Each is covered in the stress tests.

**Caveat:** All figures are illustrative assumptions for the course, not validated against real usage data.
