---
name: wave-vuln-scan
description: "Run the armed vulnerability-scan pattern: Semgrep MCP sweep plus validated manual tracing with persistent finding memory. Use for scheduled security reviews or pre-release audits."
---

# WAVE Vuln Scan

The scan pattern WAVE runs daily on its own money paths. Two passes, then memory.

## Pass 1 — Semgrep MCP sweep

If a Semgrep MCP server is available (`security_check`, `semgrep_scan`), sweep
the target repo first. Treat hits as CANDIDATES, not findings.

## Pass 2 — validated tracing

For every candidate, verify exploitability with concrete code tracing. Every
reported issue must include:

- who the attacker is
- what input they control
- how they reach the vulnerable code
- what impact they gain
- one primary file path (line details go in evidence, not the location)

Do not report speculative concerns, isolated unsafe-looking APIs without a real
attack path, or low-signal best-practice notes. Do not open a PR from this
workflow unless explicitly asked.

## Finding memory (dedup across runs)

Keep `{repo}---flagged-vulnerabilities.json` (100 findings max per file,
`-1`, `-2` overflow). Before scanning, read existing files and never
re-report a present finding. After scanning, append only genuinely new
validated findings. Never create staging/date-based scratch files.
