---
name: wave-x402-call
description: >-
  use when an agent must pay for a WAVE call via HTTP 402 / x402 (Base USDC)
  without a WAVE API key
meters: []
endpoints:
  - https://api.wave.online/mcp
  - https://wave.online/.well-known/x402
tools: [facilitator_status, list_supported_protocols]
---
# wave-x402-call

Agent path (no key):

1. Call capability (MCP or OpenAPI).
2. On **402**, treat challenge body as authoritative payment terms.
3. Settle x402 (Base USDC); retry with protocol credential header.
4. Report settle errors honestly — never invent a paid receipt.

Do not confuse person-path `SPEND_CAP_TIER_BLOCKED` (needs card) with x402.
