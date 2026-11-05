# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | OpenAI | H | Set up and test API access with a second model provider, so it's available if needed |
| **Abstraction** | A layer sits between the feature code and OpenAI | L | Check whether the abstraction layer can call a second model with a test request, to measure how much would need to change |
| **Routing** | Switching to another model requires a code change. No fallback: drafting stops if OpenAI is unavailable | H | Move model selection into configuration so a fallback model can be switched without a code change (developer task) |
| **Eval** | Manual test review, monthly. No automated eval set | H | Create a small set of test reviews with agreed quality standards, and run it whenever the model or prompts change |

## Portability Score
Partial. An abstraction layer exists, but switching models needs a code change, there is no fallback, and quality is checked only by monthly manual review.

## If OpenAI doubles pricing tomorrow:
Absorb the cost. Switching models within 48 hours isn't realistic, since it requires a code change and there is no tested alternative.

## If OpenAI ships a competing product:
What's defensible that they can't replicate:
- Learning content
- Feedback context
- Objective and development activity content
