# WAVE Cursor / Agent Plugin

**Media MCP for agents: captions, clips, render, live — pay with key or x402.**

Also: *96 media tools. One remote MCP. Dual-402 (API key or Base USDC).*

Surface: `wave-agent-plugin` (INTENT). Plugin packaging is unmetered; tool calls re-enter the WAVE gateway meters (`wave_transcription_minutes`, `wave_render_minutes`, `wave_caption_minutes`, …).

## Connect

Remote MCP (authority projection of the API):

- `https://api.wave.online/mcp`
- Discovery: `https://wave.online/.well-known/mcp.json`
- OpenAPI authority: `https://api.wave.online/openapi.json`

## Dual auth

| Path | Who | How |
|------|-----|-----|
| **Agent / x402** | autonomous agents | Call with **no** API key → HTTP **402** challenge → settle Base USDC → retry. No WAVE account. |
| **Person / Bearer** | humans / orgs | Optional `WAVE_API_KEY` → `Authorization: Bearer …`. Cost-heavy routes may require a card (`SPEND_CAP_TIER_BLOCKED`). |

`WAVE_API_KEY` is **optional** and must **not** be required to install or connect. Never commit keys.

## Skills (lean matrix)

| Skill | Tools / endpoints | Meters |
|-------|-------------------|--------|
| `wave-media` | `facilitator_status`, discovery | [] |
| `wave-transcribe` | `wave_*` transcribe / `POST /v1/transcribe` | `wave_transcription_minutes` |
| `wave-captions` | `wave_*` captions | `wave_caption_minutes` |
| `wave-render` | `wave_render_video` / poll | `wave_render_minutes` |
| `wave-clips` | `wave_*` clips | (gateway) |
| `wave-x402-call` | 402 settle/retry | per challenge |
| `wave-openapi` | points at OpenAPI JSON | n/a |

Four-renderings law: **API is authority**; MCP/CLI/SDK are projections. Skills teach *when/how to call* — they are not a fifth semantic path. Do not invent transcripts, captions, receipts, or tools.

## Layout

```
.cursor-plugin/plugin.json
plugin.json
mcp.json
skills/*/SKILL.md
README.md
```

## States

`unconnected` → `connected-no-key` → (`connected-with-key` | `payment-required-402`)

## License

MIT
