# Predecessor evidence: what the AskOverlay project measured

Status: reference. Source of truth is the `askoverlay` repository; this page is a summary so this repository stands on its
own. Source commit for the import: tag `archive/sapienzero-plan-v0.1` in `github.com/brindeshwar/askoverlay`.

## Why this page exists

SapienZero was spun out of AskOverlay ([ADR-0001](../decisions/0001-pivot-to-an-ai-test-agent.md)). Some of that work
carries over as **method** and as **evidence**. The code itself does not live here (open question OQ-03).

## The one experiment (EXP-001): can a vision model point at the right control?

Recorded in the predecessor as
[AskOverlay decision 0008](https://github.com/brindeshwar/askoverlay/blob/archive/sapienzero-plan-v0.1/docs/decisions/0008-product-direction-show-me-where.md).

- **Setup:** 20 real screenshots from the owner's own applications, 60 AI-suggested questions, two models judged blind and
  shuffled on 115 boxes by one person. A model that gave no usable answer counts as wrong. Ranges are 95% confidence.
- **Pre-registered rule, fixed before judging:** at least 30 judged answers and 8 button-sized boxes per model; GO needs 85% on
  the right control and 60% right-and-tight; 70 to 85% is MITIGATE; below 70% is RETHINK.
- **Result:** both lite models pass the rule. Right control: 87% (76 to 93%) and 85% (74 to 92%); right and tight: 80% and 73%.
  On button-sized controls only, about 80%. Larger targets were right 17 of 17, which lifts the headline average.
- **Limits:** one judge who also chose the questions, all questions AI-suggested, 20 screenshots from one person's apps, a
  free-tier key, one day. It is human-judged, not independent ground truth.
- **What may be claimed:** "points at the right control about 85% of the time on 20 real screens (n=60); about 80% for
  button-sized controls." Nothing stronger.

An earlier scored run was **inconclusive** because the labelled boxes were regions (a random click would already score 40%),
and the decision rule correctly refused a verdict. That behaviour is the template for our own evaluation rules.

## What carries over

| Carries over | How it is used here |
|---|---|
| The evaluation method: pre-registered bars, blind judging, honest confidence ranges, refusal to rule on small or coarse samples | [Evaluation strategy](evaluation-strategy.md) |
| Provider-neutral model access, a fallback model, error classification (rate limit, timeout, connection, invalid request, authentication, server) | Model gateway in the [LLD](../04-architecture/lld.md) |
| Two lite models as a cheap default (a primary and a fallback) | Open question OQ-05 |
| The pointing capability, about 80% on small controls | The R3 vision fallback; it must be re-measured on our own test bed before any claim |

## What does not carry over

The desktop overlay interface, the per-device demo quota and per-IP caps, and the original product direction ("show me where").

## Private data

The predecessor's raw evaluation data (screenshots, questions, judgments) is private and is **not** in either repository.
Only the aggregates above are public.
