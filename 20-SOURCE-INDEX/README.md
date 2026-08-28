# Discord Source Index

## Source identity

**Repository:** `KNOBALL-INTELLIGENCE/Discord-archive`

**Current tenant/source:** `KNOBALL PILOT`

**Role:** raw Discord intake and evidence source.

## Current authoritative raw baseline

- Archive ID: `2026-08-27_22-36-34_EDT_27c51364`
- Server ID: `1530755751318917224`
- Full-server messages: 12,019
- Channels processed: 132
- Errors: 0

Source:
`discord-archives/2026/08/27/2026-08-27_22-36-34_EDT_27c51364/KNOBALL_PILOT_FULL_SERVER_2026-08-27_22-36-25.json`

## Known targeted export

- Archive ID: `2026-08-27_22-27-28_EDT_d209bc4b`
- Channel: `🔝general-kb-pilot`
- Messages: 4

## Knoball routing model

`Discord -> Discord-archive -> normalize/dedupe -> source/delta registration -> SARA reconciliation -> authoritative owning Workbench/tenant surface`

### Enterprise archive relationship

`WORKBENCH-ARCHIVES` is the natural enterprise owner for archive/index/reference registration and provenance.

The raw 13 MB+ payload does not need to be copied into every Workbench repository. Workbench should point back to source evidence.

### League relationship

For now, the Pilot does not have its own clean tenant repository. When one is established, cleaned league state may be migrated there with:
- source archive ID;
- Discord server/channel/message identifiers;
- source commit/path;
- reconciliation status;
- authority/currentness status.

### Drive relationship

Drive may provide human-facing working/navigation artifacts, but Drive copies do not replace the raw source or create independent currentness authority.

## Classification boundary

Discord material can be classified as:
- evidence;
- discussion;
- proposal;
- decision candidate;
- decision evidence;
- operational history;
- test result;
- issue/bug evidence;
- league-specific knowledge;
- enterprise-relevant knowledge.

Classification is not promotion.

Any material effect on current rules, roadmaps, architecture, economics, permissions, policy, or other governed state still follows the authority/currentness model of the owning Knoball surface.
