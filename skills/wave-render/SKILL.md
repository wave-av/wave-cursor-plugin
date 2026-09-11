---
name: wave-render
description: use when rendering programmatic video via WAVE (Brief templates, wave_render_video)
meters: [wave_render_minutes]
endpoints:
  - POST /v1/render
  - GET /v1/render/{jobId}
tools: [wave_render_video, wave_render_poll]
---
# wave-render

Programmatic render via `wave_render_video` / `wave_render_poll` (or OpenAPI `/v1/render`). Meter: `wave_render_minutes`.

Auth: Bearer or x402. Do not invent render outputs or receipts.
