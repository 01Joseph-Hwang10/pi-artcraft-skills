# NOTICE

This repository (`01Joseph-Hwang10/pi-artcraft-skills`) is an unofficial,
community-maintained [Pi](https://pi.dev) package that republishes the skills
from [`midasmatterhorn/artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills)
for the Pi coding agent.

## Scope of the licenses

The MIT OR Apache-2.0 dual license in `LICENSE-MIT` and `LICENSE-APACHE`
covers **this repository's own packaging content only**: `package.json`, this
`NOTICE.md`, the `README.md`, and the governance files under `specs/`.

The **skills themselves** (`skills/*/SKILL.md`, `skills/*/evidence.md`,
`skills/*/references/`) are **not relicensed here**. They are
portions of the upstream repository
[`midasmatterhorn/artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills)
and remain **© midasmatterhorn, licensed MIT** (see the upstream `LICENSE`).
This package distributes them unmodified, except for a single
`license: MIT` line added to each skill's `SKILL.md` frontmatter to satisfy
the [Agent Skills specification](https://agentskills.io) `license` field.

The ArtCraft applications that these skills teach agents to operate are
independent software with their own terms; these skills contain no third-party
or Adobe assets and are clean-room documentation.

## Trademarks

The ArtCraft name, wordmark, and logos, as well as the individual Craft App
names (FigCraft, DeckCraft, PhotoCraft, and the rest), are trademarks of the
ArtCraft Team. They are used here solely to describe, in good faith, which
upstream software each skill documents, and this package is not affiliated
with, endorsed by, or sponsored by the ArtCraft Team.

## Port provenance

- Upstream: <https://github.com/midasmatterhorn/artcraft-skills> (MIT)
- Ported at upstream tag **v1.0.5**, commit **`5706b6a184d955aeace671c5de4bfbc27f296682`**
- Dropped relative to upstream: `agents/openai.yaml` sidecars (Codex/ChatGPT
  UI metadata — Pi discovers skills natively via the Agent Skills standard),
  `install.sh` / `install.ps1` (Pi installs packages itself), `assets/`
  (icons and marquee — unused in this distribution), and the upstream
  `AGENTS.md` (superseded by Pi package discovery)
