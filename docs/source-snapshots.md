# Local source snapshots

The analyzer verifies this profile against four pinned source snapshots. They
are excluded from Git because this repository does not redistribute the
upstream mods. Obtain authorized copies from their Workshop pages, or copy the
matching snapshots from a local Europa Concordia checkout, into these paths:

| Package                       | Workshop item | Required local directory                            |
| ----------------------------- | ------------- | --------------------------------------------------- |
| Community Mod Framework 2.5.0 | 3692202776    | `sources/steam-workshop/3692202776/`                |
| More locations Mod 2.10.2026  | 3809335454    | `sources/steam-workshop/3809335454/`                |
| Global Historical RGOs 1.4.0  | 3602513956    | `sources/steam-workshop/3602513956-2026-11-23/`     |
| Just Goods 1.1.0              | 3785316314    | `sources/steam-workshop/3785316314-1.1-2026-11-23/` |

The expected tree checksums are pinned in
[`profiles/rgo-harmony.json`](../profiles/rgo-harmony.json) and
[`config/packages.json`](../config/packages.json). Validation fails rather
than silently accepting a different source tree. Do not commit snapshots;
`sources/steam-workshop/` is ignored.

Vanilla game files are read from the local EU5 installation and remain
read-only. Do not copy vanilla files into this repository.
