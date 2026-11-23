# CMT Workshop gallery synchronization

## Context

The upstream Community Mod Toolkit release used by this project does not
provide an uploader option for synchronizing Workshop gallery images. The RGO
Harmony adapter already stages validated images when `--sync-gallery` is
requested, so the generated uploader must also support that operation.

## Decision

Maintain the gallery support as a separate patch at
[`integration/patches/cmt-gallery-sync.patch`](../patches/cmt-gallery-sync.patch).
It targets CMT `toolkit-release` commit
`73080c47f6d7667bf899af276ffd0e3674f53a64`. During CMT preparation, the
adapter applies it to a temporary copy of `tools/upload.py` and
`tools/steamworks`; the imported toolkit checkout is never modified. The
patched files are copied only into the ignored generated CMT workspace, not
into the EU5 mod or Workshop release payload.

Gallery changes are opt-in. The uploader validates JPG, JPEG, and PNG images
smaller than 1 MB, stages them in filename order, replaces existing image
previews, and preserves the primary thumbnail and non-image previews. A
missing or empty gallery is rejected before upload. Ordinary publishing
without `--sync-gallery` does not change gallery images.

The patch is a GPL-3.0-only modification of the CMT toolkit. Its license is
included in [`integration/patches/GPL-3.0.txt`](../patches/GPL-3.0.txt).

## Validation

The patch is checked against the pinned toolkit release in a temporary
directory. CMT preparation with `--sync-gallery` must produce a gallery-aware
uploader and stage the selected images. Preparation itself never uploads.
