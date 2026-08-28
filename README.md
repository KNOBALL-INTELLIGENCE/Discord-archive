# Knoball Discord Archive

This repository is the raw Discord intake and evidence home for the **KNOBALL PILOT** server while the Pilot remains the active reference implementation for future league onboarding.

## Start here

- **[Pilot Server Guide](00-PILOT-SERVER/README.md)** — human-facing entry point for the boys.
- **[Pilot Baseline](10-INGEST-STATE/PILOT-BASELINE.json)** — current full-server ingest checkpoint and deduplication identity.
- **[Ingest & Deduplication Rules](10-INGEST-STATE/README.md)** — how overlapping exports are handled.
- **[Source Index](20-SOURCE-INDEX/README.md)** — provenance and routing into Knoball/SARA/Workbench.
- **[Raw Discord Exports](discord-archives/)** — untouched exporter output.

## Current Pilot baseline

The initial full-server baseline was captured on **August 27, 2026**.

- Server: `KNOBALL PILOT`
- Discord server ID: `1530755751318917224`
- Archive ID: `2026-08-27_22-36-34_EDT_27c51364`
- Channels processed: **132**
- Messages captured: **12,019**
- Export errors: **0**

[Open the baseline full-server JSON](discord-archives/2026/08/27/2026-08-27_22-36-34_EDT_27c51364/KNOBALL_PILOT_FULL_SERVER_2026-08-27_22-36-25.json)

## What lives here

`discord-archives/` is append-only source evidence. Timestamped exports are preserved exactly as uploaded, even when later exports overlap them.

The organized files at the repository root are navigation and ingest-state records. They do **not** replace or rewrite the raw Discord evidence.

## Overlapping uploads

Repeated full-server, channel, thread, or message-range exports are expected. Logical Discord messages are deduplicated using:

`server_id + channel_id + message_id`

A repeated identical message is already-seen evidence, not a second message. The same message ID with changed content or metadata is treated as a revision and preserves lineage back to each source archive.

## Knoball integration boundary

This repository preserves Discord evidence. Discord conversation is **not automatically Knoball canon, policy, or a league decision**.

Normalized/new Discord deltas may be routed through SARA for comparison with current Knoball Workbench and Drive material. Durable league or enterprise state belongs with the authoritative owning repository/surface, with provenance back to the Discord source.

## Future direction

For now, this repository remains the Pilot server's intake home. The Pilot will eventually receive its own league repository. What we learn here will inform:

- future per-league repository templates;
- 100 League repository review/restructuring proposals;
- league onboarding and full-server import;
- incremental Discord maintenance;
- league-specific knowledge/filter generation;
- downstream Knoball/Noble integration.

Raw evidence stays here; cleaned tenant knowledge migrates only through an explicit reconciled process.
