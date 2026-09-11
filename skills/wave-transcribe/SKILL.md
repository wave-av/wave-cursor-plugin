---
name: wave-transcribe
description: use when transcribing audio or video with WAVE (speech-to-text)
meters: [wave_transcription_minutes]
endpoints:
  - POST /v1/transcribe
tools: [wave_create_transcription, wave_get_transcription, wave_list_transcriptions]
---
# wave-transcribe

Speech-to-text via WAVE MCP tools or `POST /v1/transcribe`. Meter: `wave_transcription_minutes` (gateway re-entry).

Auth: optional Bearer **or** unpaid → 402 → x402 settle → retry (`wave-x402-call`). Never invent transcripts.
