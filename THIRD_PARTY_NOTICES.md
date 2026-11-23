# Third-party notices

RGO Harmony requires these separate Workshop mods. Their source snapshots are
not included in this repository or in the generated compatibility mod.

| Mod                     | Author                  | Workshop item                                                                   |
| ----------------------- | ----------------------- | ------------------------------------------------------------------------------- |
| Community Mod Framework | Community Mod Framework | [3692202776](https://steamcommunity.com/sharedfiles/filedetails/?id=3692202776) |
| More locations Mod      | Naaku                   | [3809335454](https://steamcommunity.com/sharedfiles/filedetails/?id=3809335454) |
| Global Historical RGOs  | Enrar                   | [3602513956](https://steamcommunity.com/sharedfiles/filedetails/?id=3602513956) |
| Just Goods              | moveably                | [3785316314](https://steamcommunity.com/sharedfiles/filedetails/?id=3785316314) |

No upstream license is recorded for these mods. The repository records the
owner's explicit permission to distribute the RGO compatibility patch,
including the merged More Locations location-template data. The compatibility
decision and its scope are documented in
[`integration/decisions/RGO-Harmony-Design.md`](./integration/decisions/RGO-Harmony-Design.md)
and in the pinned package attribution notices in
[`config/packages.json`](./config/packages.json). Do not add or distribute
upstream source files without the respective authors' permission.

The Community Mod Toolkit is maintained separately at
[Europa-Universalis-5-Modding-Co-op/community-mod-toolkit](https://github.com/Europa-Universalis-5-Modding-Co-op/community-mod-toolkit);
it is installed locally for CMT operations and is not bundled here. The
maintained [gallery-sync patch](./integration/patches/cmt-gallery-sync.patch)
is a GPL-3.0-only modification of the toolkit, applied only to generated local
CMT workspaces. Its license is included at
[`integration/patches/GPL-3.0.txt`](./integration/patches/GPL-3.0.txt); neither
the toolkit nor the patch is included in the generated EU5 mod.
