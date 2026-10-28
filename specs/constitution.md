# Constitution — pi-artcraft-skills

Governing principles for every change in this repository. Amendments require a
new entry in `specs/changes/`.

## 1. Spec-driven workflow

- No implementation starts without a plan under `specs/changes/<NNN>--<slug>/plan.md`.
- Each change gets its own numbered directory; completed changes are never edited
  retroactively — corrections go into a new change directory.
- This constitution lives in `specs/constitution.md` and outranks any plan.

## 2. Ported, not re-authored

- `skills/*` content is a port of
  [`midasmatterhorn/artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills)
  and stays **byte-identical** to upstream, except the single
  `license: MIT` frontmatter line required by the Agent Skills specification.
- Skill content is never edited independently of upstream. Upstream fixes flow
  in as ports; local fixes must land upstream first, then be ported here.
- Every port records its upstream tag and commit in `NOTICE.md` (Port
  provenance). Updating the port without updating that record is forbidden.
- The npm package version equals the upstream tag it was ported from
  (`v<version>`), which is the single source of truth. Re-publishing with a
  version that has no upstream tag, or updating the port without bumping the
  version to the new upstream tag, is forbidden.

## 3. Upstream respect (fail closed)

- A port update must diff cleanly against the recorded upstream commit:
  any unexplained divergence between `skills/*` here and upstream at the
  recorded commit fails review.
- Upstream skills are never silently dropped, renamed, or reorganized. If
  upstream renames or restructures a skill, the change is ported explicitly
  with a documented mapping.

## 4. Pi-specific deltas are enumerated

- The only allowed deviations from upstream are listed in the README's
  *Port fidelity* section and `NOTICE.md` (currently: the `license: MIT`
  frontmatter line; dropped `agents/openai.yaml`, installers, `assets/`, and
  upstream `AGENTS.md`). Adding a new deviation (e.g. Pi
  frontmatter fields, split references) requires a change directory and a
  README/NOTICE update in the same change.
- The package is a pure skills package: no extensions, no prompt templates,
  no themes, no executable code. `package.json` carries no `dependencies`.

## 5. Integrity gates

- A change is done only when:
  - `pi -e ./` starts with no skill warnings (run from a scratch directory),
  - every `skills/*/SKILL.md` parses (frontmatter intact, `name` matches the
    directory, `description` present, `license: MIT` present),
  - `npm pack --dry-run` includes exactly `skills/`, README,
    NOTICE, and both LICENSE files.
- CI (when added) must re-verify these gates and fail on drift.

## 6. Licensing

- This repository's own content (packaging, README, NOTICE, specs) is
  dual-licensed MIT OR Apache-2.0 (`LICENSE-MIT`, `LICENSE-APACHE`).
- Skill content remains © midasmatterhorn, MIT — never
  relicensed, never re-copyrighted. `NOTICE.md` is the single source of truth
  for this scope split; keep it accurate in every change.

## 7. Attribution

- The README's *note to the original author* and the upstream link must stay
  present and accurate. Removing attribution is forbidden.
