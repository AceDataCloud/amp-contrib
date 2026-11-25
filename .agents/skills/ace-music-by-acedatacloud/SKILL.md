---
name: ace-music-by-acedatacloud
description: Use ACE Music tools to create songs from a prompt or custom lyrics, upload reference audio, cover or blend owned tracks, and retrieve original task results.
license: Apache-2.0
---

# ACE Music by Ace Data Cloud

Start Amp with your Ace application token in `ACEDATACLOUD_API_TOKEN`. The sibling `mcp.json` connects to the hosted ACE Music service. See the [English setup guide](https://github.com/AceDataCloud/Skills/blob/2692ba6bc199b4b57b24e14ea59f25574ee71364/platforms/amp/skills/ace-music-by-acedatacloud/README.md) or [中文安装指南](https://github.com/AceDataCloud/Skills/blob/2692ba6bc199b4b57b24e14ea59f25574ee71364/platforms/amp/skills/ace-music-by-acedatacloud/README.zh-CN.md).

Use `acemusic_list_models` and `acemusic_get_capabilities` for discovery. A song request creates two candidate tracks. Use `acemusic_generate_music` for an idea or `acemusic_generate_custom_music` when the user provides a title, lyrics and style. The default is `acemusic-v1.1` and `acemusic-v1` also supports ordinary generation. Create separate lyrics with `acemusic_generate_lyrics` when requested.

For reference work, `acemusic_upload_audio` imports one publicly accessible HTTPS MP3 as a separately priced operation. Use `acemusic_cover_audio` for one owned platform audio ID, or `acemusic_mashup_audio` for two distinct compatible owned audio IDs. These operations use `acemusic-v1.1` with lyrics and style. An audio ID identifies a track in the completed task; a task ID identifies the request. Confirm the user's intended action and consult [current pricing](https://platform.acedata.cloud/services/acemusic) before spending.

Save the original task ID and call `acemusic_get_task` until that task finishes. Batch lookup and history are available through `acemusic_get_tasks_batch` and `acemusic_list_tasks`. Authenticated task queries are free. For `succeeded`, return completed tracks and their URLs. For `partial_failed`, identify surviving tracks and report the partial result. For `failed`, report the error. For `submission_unknown`, keep the same task ID for reconciliation. Avoid paying for a duplicate request after a timeout.
