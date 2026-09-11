---
name: wave-captions
description: use when creating or downloading WAVE captions / subtitles for media
meters: [wave_caption_minutes]
endpoints:
  - /v1/captions
tools: [wave_create_caption_job, wave_get_caption_job, wave_download_captions, wave_list_captions]
---
# wave-captions

Caption/subtitle jobs via WAVE MCP or `/v1/captions*`. Meter: `wave_caption_minutes`.

Return real job status / SRT|VTT downloads only — never fabricate subtitle text.
