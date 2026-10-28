# pi-artcraft-skills

A [Pi](https://pi.dev) port of [`midasmatterhorn/artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills): thirteen evidence-verified skills for the [ArtCraft](https://getartcraft.com) creative suite, packaged as one installable Pi package.

The skills teach the Pi coding agent to drive the ArtCraft apps through their first-class automation surfaces (headless CLI, MCP server, JSON control channel) rather than blind GUI automation. All credit for the skill content itself goes to the original author — this repo is only the Pi distribution.

## Install

```sh
pi install npm:pi-artcraft-skills
```

Then restart your Pi session. Skills trigger when you mention an app or its file formats (`.psd`, `.pptx`, `.xlsx`, `.docx`, `.dxf`, …), or force one with `/skill:photocraft`.

## The skills

`cadcraft`, `deckcraft`, `designcraft`, `effectcraft`, `figcraft`, `filmcraft`, `gridcraft`, `lightcraft`, `pdfcraft`, `photocraft`, `soundcraft`, `vectorcraft`, `wordcraft` — one per ArtCraft app. See the [upstream README](https://github.com/midasmatterhorn/artcraft-skills#the-skills) for the full table, per-app descriptions, and the pinned app commit each skill was verified against.

## Port fidelity

Distributed byte-identical to upstream, except:

- `license: MIT` added to each `SKILL.md` frontmatter (agentskills.io spec field).
- Dropped: `agents/openai.yaml` (Codex UI metadata), `install.sh` / `install.ps1` (Pi installs packages itself), `assets/` (unused here), upstream `AGENTS.md`.

Provenance (upstream tag + commit) is recorded in [`NOTICE.md`](NOTICE.md).

## Licensing

- This repo's own packaging content: MIT OR Apache-2.0 — [`LICENSE-MIT`](LICENSE-MIT) / [`LICENSE-APACHE`](LICENSE-APACHE).
- The skills: not relicensed here; they remain © midasmatterhorn, MIT. See [`NOTICE.md`](NOTICE.md).

## A note to the original author

> **Hi midasmatterhorn!** This package is an unofficial, community-maintained port of your [`artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills) to Pi, so Pi users get your thirteen skills with one `pi install` command. The skills are distributed byte-identical to your upstream work, tracked one-to-one rather than forked.
>
> If you're interested, I'd happily hand this repository over so the Pi distribution becomes official, or coordinate however works best — for example, a skills layout or package manifest upstream that this repo could simply track.
>
> To get in touch: [@01Joseph-Hwang10](https://github.com/01Joseph-Hwang10) — open an issue here or on upstream. Thank you for the superb original work.
