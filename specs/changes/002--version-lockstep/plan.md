# Change 002 — Version lockstep with upstream

**Status:** done

## Goal

Make this package's npm version track the upstream
[`artcraft-skills`](https://github.com/midasmatterhorn/artcraft-skills) tag
one-to-one, so `pi-artcraft-skills@X.Y.Z` always corresponds to upstream
`vX.Y.Z` (mirroring the `artcraft-cli-homebrew-tap` convention).

## Constitution amendment

New rule 2a under *Ported, not re-authored* in `specs/constitution.md`:

> The npm package version equals the upstream tag it was ported from
> (`v<version>`), which is the single source of truth. Re-publishing with a
> version that has no upstream tag, or updating the port without bumping the
> version to the new upstream tag, is forbidden.

## Implementation

- Bump `package.json` `0.1.0` → `1.0.5` (upstream tag `v1.0.5`, commit
  `5706b6a`, already the ported basis — see `NOTICE.md`).
- Publish `pi-artcraft-skills@1.0.5` to npm.

## Verification

- Registry serves `1.0.5` under the `latest` dist-tag.
- No `package.json` field other than `version` changed.
