---
title: Notetaker API
section: notetaker
---

## Notetaker API

AI meeting recording, transcription, summaries, and action items. Supports **Google Meet**, **Microsoft Teams**, and **Zoom**.

### Endpoints

| Endpoint | Purpose |
|----------|---------|
| `POST /v3/grants/{id}/notetakers` | Create grant-scoped notetaker |
| `GET /v3/grants/{id}/notetakers` | List notetakers |
| `GET /v3/grants/{id}/notetakers/{id}` | Get notetaker details |
| `PATCH /v3/grants/{id}/notetakers/{id}` | Update notetaker |
| `DELETE /v3/grants/{id}/notetakers/{id}/cancel` | Cancel scheduled notetaker |
| `DELETE /v3/grants/{id}/notetakers/{id}` | Permanently delete |
| `POST /v3/grants/{id}/notetakers/{id}/leave` | Remove from active meeting |
| `GET /v3/grants/{id}/notetakers/{id}/media` | Get recording/transcript media |
| `GET /v3/grants/{id}/notetakers/{id}/history` | Status history (troubleshooting) |
| `POST /v3/notetakers` | Standalone notetaker (no grant) |

### Media Output

| Type | Format |
|------|--------|
| Recording | MP4 video, or MP3 when `audio_recording=true` and `video_recording=false` |
| Transcript | JSON speaker-labelled transcript, with a rare raw-text fallback |
| Thumbnail | PNG (video recordings only) |
| Summary | JSON (AI-generated) |
| Action items | JSON (AI-generated) |

### AI Features

- Auto-generated meeting summaries
- Auto-generated action items
- Custom instructions via `summary_settings.custom_instructions` and `action_items_settings.custom_instructions`

### Silence Detection

Notetaker leaves after 5 minutes (300s) of silence by default. Configurable via `leave_after_silence_seconds` (10-3600s).

Media URLs in `notetaker.media` payloads are pre-authenticated and valid for 60 minutes. Fetch the media endpoint again to regenerate expired URLs.

### Webhook Triggers

`notetaker.created`, `notetaker.updated`, `notetaker.meeting_state`, `notetaker.media`, `notetaker.deleted`

### Integration Features

| Feature | Doc Link |
|---------|----------|
| Calendar sync (auto-join meetings) | https://developer.nylas.com/docs/v3/notetaker/calendar-sync/ |
| Media handling (recordings, transcripts) | https://developer.nylas.com/docs/v3/notetaker/media-handling/ |
| Scheduler integration | https://developer.nylas.com/docs/v3/notetaker/scheduler-integration/ |

Reference: [Notetaker docs](https://developer.nylas.com/docs/v3/notetaker/)
