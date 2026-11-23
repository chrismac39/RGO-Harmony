# RGO Harmony

RGO Harmony is a standalone EU5 compatibility mod for Community Mod Framework,
More Locations, Global Historical RGOs, and Just Goods. It keeps More Locations
as the map base, applies the approved Global Historical RGO values at the
reviewed conflicts and descendants, and leaves Just Goods' startup effects
intact.

The generated mod contains the compatibility payload and launcher metadata,
not bundled copies of the required upstream mods. The map-template merge is
maintained separately in
[`integration/patches/`](./integration/patches/). The recorded compatibility
decisions and attribution are in
[`integration/decisions/`](./integration/decisions/) and
[`THIRD_PARTY_NOTICES.md`](./THIRD_PARTY_NOTICES.md).

## Requirements

- Node.js 22 or newer and npm
- EU5 1.4.9 installed locally for game-aware validation
- The four pinned source snapshots locally available under the ignored
  `sources/steam-workshop/` directory; see
  [`docs/source-snapshots.md`](./docs/source-snapshots.md)

## Validate and build

```powershell
npm ci
npm run analyze -- --profile rgo-harmony
npm run validate -- --profile rgo-harmony
npm test
npm run build -- --profile rgo-harmony
```

The generated mod is under `dist/rgo-harmony/rgo-harmony/`. Analysis output is
under `reports/rgo-harmony/`; review it and require zero unresolved findings
before packaging. Static validation is not a substitute for in-game testing.

For a local launcher install, run:

```powershell
npm run workshop:install -- --profile rgo-harmony
```

This only copies the validated mod to the local EU5 mod directory; it does not
upload or publish anything.

## CMT Workshop workflow

This repository includes the Community Mod Toolkit (CMT) adapter, profile
configuration, Workshop description, release notes, and preparation/publish
instructions. CMT itself is installed locally and is not vendored. See
[`docs/workshop-publishing.md`](./docs/workshop-publishing.md).

The configured Workshop target is the existing item `3833870015`; the explicit
publish command updates that item. Build and validation never upload anything.

## Project layout

- `profiles/`: pinned Harmony inputs and standalone mod metadata
- `integration/patches/`: maintained compatibility payload
- `integration/decisions/`: design, source audits, and release decisions
- `integration/workshop/rgo-harmony/`: Workshop page, thumbnail, gallery, and
  versioned change notes
- `scripts/`: analysis, build, validation, local install, and CMT adapter
- `config/`: package pins, conflict decisions, build routing, and Workshop ID
- `sources/`, `reports/`, `dist/`, `.local/`: ignored local inputs/tools/output
