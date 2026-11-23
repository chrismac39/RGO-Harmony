# Workshop publishing with CMT

## Target and release boundary

The CMT configuration targets the existing RGO Harmony Workshop item
`3833870015`. A publish updates that item; it is not an isolated/private test
item. The user selected this target. CMT does not configure visibility, so
verify the item and its visibility in Steam after publishing.

Analysis, validation, build, local installation, and CMT preparation do not
upload anything. Only the explicit `publish` command can invoke the uploader,
and it requires a confirmation token immediately before upload.

## Install CMT locally

CMT and its Python dependencies stay outside version control under ignored
`.local/`:

```powershell
New-Item -ItemType Directory -Force .local | Out-Null
git clone --branch toolkit-release --single-branch `
  https://github.com/Europa-Universalis-5-Modding-Co-op/community-mod-toolkit.git `
  .local\community-mod-toolkit
python -m venv .local\cmt-venv
.local\cmt-venv\Scripts\python.exe -m pip install `
  -r .local\community-mod-toolkit\tools\dependencies\requirements.txt
```

Keep Steam authentication in Steam itself. Never place passwords, tokens,
Steam Guard codes, or SteamCMD session files in this repository or generated
artifacts.

## Prepare and inspect

Run analysis, validation, tests, and build first:

```powershell
npm run analyze -- --profile rgo-harmony
npm run validate -- --profile rgo-harmony
npm test
npm run build -- --profile rgo-harmony
npm run workshop:cmt -- prepare --profile rgo-harmony `
  --toolkit-dir .local\community-mod-toolkit
```

Preparation produces an isolated CMT project under
`dist/cmt-workspaces/rgo-harmony/project`. Inspect its generated mod, title,
thumbnail, description, required items, and versioned change notes. Confirm
that the analysis has zero unresolved findings, the release payload contains
only the declared compatibility files, the attribution/permission records
are present, and the change notes match this profile's version.

## Explicit publish

After review, use the explicit command below. It rebuilds and stages the
profile, then requires the exact confirmation token immediately before CMT
starts. The command uploads to the configured existing item:

```powershell
npm run workshop:cmt -- publish --profile rgo-harmony `
  --toolkit-dir .local\community-mod-toolkit `
  --python .local\cmt-venv\Scripts\python.exe `
  --confirm-publish "PUBLISH rgo-harmony UPDATE"
```

Do not run this command without a final human confirmation for this release.
After upload, verify the item, release notes, required items, images, and
visibility on Steam. CMT publishing does not establish in-game correctness;
runtime verification remains outstanding until tested in EU5.
