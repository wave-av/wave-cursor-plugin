# wave-cursor-plugin

WAVE agent plugin for Cursor (Agent Plugins open standard): review-plane and
vuln-scan skills. Secret-free by design — callers supply their own
`REVIEW_PLANE_KEY`.

## Contents

- `plugin.json` — Agent Plugins manifest
- `skills/wave-review/` — multi-reviewer verdicts via the WAVE review plane
  (MCP `review`/`summarize_review` or REST `POST /v1/review`)
- `skills/wave-vuln-scan/` — the armed scan pattern (Semgrep sweep + validated
  tracing + persistent finding memory)

## Test locally

Copy this repo to `~/.cursor/plugins/local/wave-cursor-plugin` and reload the
window (or Developer: Reload Window). Confirm the skills appear under Customize.

## Publish

Marketplace submission is manual review at cursor.com/marketplace/publish.
Requires the repo public + a human submitter.
