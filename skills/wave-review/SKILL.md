---
name: wave-review
description: "Get a multi-reviewer verdict on a repo or PR from WAVE's review plane (correctness, security, cross-file, design). Use for second-opinion reviews, pre-merge gates, or auditing agent-generated code."
---

# WAVE Review

Call WAVE's review plane for a synthesized multi-reviewer verdict. No secrets in this plugin — the caller supplies their own `REVIEW_PLANE_KEY` (a tenant key from the plane's onboarding).

## Via MCP (preferred)

If the `wave-review` MCP server is configured (URL `https://review.wave.online/mcp`,
header `Authorization: Bearer <REVIEW_PLANE_KEY>`), call:

- `review` with `{ "repo": "owner/name" }` → verdict list (reviewer, verdict, evidence, price_cents)
- `summarize_review` with the verdict list → one-paragraph synthesis

## Via REST (fallback)

`POST https://review.wave.online/v1/review` with header
`Authorization: Bearer <REVIEW_PLANE_KEY>` and JSON body `{ "repo": "owner/name" }`.

## Reading the verdict

- Weight overlapping findings across reviewers more heavily.
- A finding with file:line evidence outranks a general observation.
- Cost note: each verdict returns `price_cents` (metered per reviewer that ran).
