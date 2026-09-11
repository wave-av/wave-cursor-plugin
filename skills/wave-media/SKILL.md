---
name: wave-media
description: >-
  use when discovering WAVE media MCP/API, checking facilitator_status, or
  explaining dual-402 (key or x402) before a specific media call
meters: []
endpoints:
  - https://api.wave.online/mcp
  - https://wave.online/.well-known/mcp.json
  - https://api.wave.online/openapi.json
---
# wave-media

Discovery and health for WAVE media. Prefer this before specialized skills.

## Do
1. Connect remote MCP `https://api.wave.online/mcp` (no API key required).
2. Call `facilitator_status` / discovery; confirm x402 rails live.
3. Route next: transcribe, captions, render, clips, or x402-call.

## Do not
- Invent tools, meters, transcripts, or receipts.
- Require `WAVE_API_KEY` for agent path.
