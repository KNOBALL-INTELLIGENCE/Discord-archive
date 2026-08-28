# Discord Ingest State & Deduplication

## Rule 1 — Never destroy raw evidence

Every exporter run may remain under `discord-archives/` even when it overlaps previous runs.

The archive run itself has provenance value.

## Rule 2 — Deduplicate logical messages, not archive files

A logical Discord message is identified by:

`guild_id + channel_id + message_id`

Examples:

- Same logical identity + same material payload = `ALREADY_SEEN`
- Same logical identity + changed content/material metadata = `REVISION`
- Previously unseen logical identity = `NEW`

A repeated message is not copied into cleaned state as another message.

## Rule 3 — Preserve revision lineage

If a message is edited and appears in a later export, keep:
- the logical message identity;
- prior observed revision(s);
- new observed revision;
- source archive IDs/paths for each observation.

Do not silently overwrite history.

## Rule 4 — Process deltas downstream

After the initial full-server baseline, later uploads should produce a normalized delta:
- new messages;
- revised messages;
- newly observed channels/threads;
- new attachments or material metadata changes;
- coverage/checkpoint changes.

SARA/Workbench reconciliation should consume the delta by default, not repeatedly treat the full server as new information.

## Rule 5 — Coverage is separate from truth

A later full-server export can improve coverage or validate completeness without creating duplicate knowledge.

## Recommended ingest dispositions

- `NEW`
- `ALREADY_SEEN`
- `REVISION`
- `NEW_CHANNEL_OR_THREAD`
- `COVERAGE_EXTENSION`
- `SOURCE_ONLY_NO_KNOWLEDGE_DELTA`
- `RECONCILIATION_REQUIRED`

## Deletion caution

Absence from a later export is **not enough by itself** to prove a Discord message was deleted unless the exporter/run semantics establish complete comparable coverage. Treat deletion as a separate verified condition.

## Current checkpoint

See `PILOT-BASELINE.json`.
