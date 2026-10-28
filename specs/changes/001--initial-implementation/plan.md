# Change 001 — Initial implementation: port artcraft-skills to a Pi package

**Status:** done
**Upstream basis:** `midasmatterhorn/artcraft-skills` tag `v1.0.5`, commit
`5706b6a184d955aeace671c5de4bfbc27f296682`

## Goal

Distribute the thirteen evidence-verified ArtCraft agent skills as a single
installable [Pi package](https://github.com/badlogic/pi-mono/blob/main/docs/packages.md),
`pi install npm:pi-artcraft-skills`, without re-authoring any skill content.

## Decisions

| Decision | Choice | Rationale |
|---|---|---|
| Distribution shape | Pure skills package (`skills/` conventional directory, no `pi` manifest, no extensions) | Pi discovers `skills/*` automatically; nothing here needs executable code |
| Skill content fidelity | Byte-identical to upstream + one `license: MIT` frontmatter line per `SKILL.md` | Future upstream updates diff cleanly; `license` is a spec field matching upstream's MIT license |
| `agents/openai.yaml` | Dropped | Codex/ChatGPT UI metadata; Pi-specific distribution, Pi ignores it |
| `install.sh` / `install.ps1` / upstream `AGENTS.md` | Dropped | Pi installs packages itself; Pi package discovery supersedes per-agent copy scripts |
| `assets/` | Dropped | Icons/marquee unused in this distribution; skill content needs no assets |
| Licensing | Own content: MIT OR Apache-2.0 (`LICENSE-MIT`, `LICENSE-APACHE`); skills + assets: © midasmatterhorn, MIT via `NOTICE.md` | Mirrors the `artcraft-cli-homebrew-tap` convention; never relicenses upstream work |
| Attribution | README *note to the original author* (midasmatterhorn) with hand-off offer | Mirrors the tap's *note to the ArtCraft Team* convention |

## Implementation

1. Copy `skills/<app>/` for all 13 apps (`SKILL.md`, `evidence.md`,
   `references/`) verbatim from upstream; skip `agents/` and `assets/`;
   insert `license: MIT` after the `name:` line in each `SKILL.md` frontmatter.
2. Add `package.json` (`pi-package` keyword, `files` allowlist, no
   dependencies), `README.md`, `NOTICE.md`, `LICENSE-MIT`,
   `LICENSE-APACHE`, `.gitignore`.

## Verification

- All 32 skill files diff-identical to upstream except the `license: MIT`
  line (checked with `diff`/`grep -v`).
- Each `SKILL.md` frontmatter: `name` matches directory, `description`
  present, `license: MIT` present.
- `npm pack --dry-run` includes exactly `skills/`, README, NOTICE,
  LICENSE-MIT, LICENSE-APACHE.
- `pi -e ./` loads all 13 skills without warnings.
