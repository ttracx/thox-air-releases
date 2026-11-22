# ThoxAir™ release list

[![License](https://img.shields.io/badge/license-Apache--2.0-171719)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/ttracx/thox-air-releases?color=171719)](https://github.com/ttracx/thox-air-releases/commits/main)
[![List](https://img.shields.io/badge/list-thoxair--update--feed%2F1-05A451)](feed.json)
![THOX](https://img.shields.io/badge/THOX-05A451)

The public list of ThoxAir releases: versions, dates, release links and SHA-256 checksums. This
repository holds the list only. It has no source code and no downloads.

Your AI. Your Data. Your Rules.™

## Preview

No product previews yet. See [docs/previews/](docs/previews/) — screenshots are added only when they
reflect the actual shipped product.

## Quick start

```sh
curl -fsSL https://raw.githubusercontent.com/ttracx/thox-air-releases/main/feed.json
curl -fsSL https://raw.githubusercontent.com/ttracx/thox-air-releases/main/release-feed.json
```

## The list

[`feed.json`](feed.json), at a stable address:

```
https://raw.githubusercontent.com/ttracx/thox-air-releases/main/feed.json
```

| Release line | Newest listed | Published | Status |
| --- | --- | --- | --- |
| `air-nano` | 0.1.0 | 2026-11-22 | proof of concept |

Everything listed so far is a proof of concept on the `preview` channel. It is not a product
release. The list also gives the exact size and SHA-256 of the optional packages and of the
whole-card image for that line. Format: [docs/FORMAT.md](docs/FORMAT.md).

## Downloads

This repository has no downloads. The update, package and image files in `feed.json` are kept in
the private provisioning bucket and are installed with the ThoxAir provisioning tools. Check any
file you are given against the SHA-256 values in this list. Steps:
[docs/USER_GUIDE.md](docs/USER_GUIDE.md).

## The signed files a ThoxAir reads

For each release line there is a folder (today: [`air-nano/`](air-nano/)) holding `release.json`,
`packages.json` and a signature for each. A ThoxAir built with this address asks for
`https://raw.githubusercontent.com/ttracx/thox-air-releases/main/<release line>/release.json`, checks the signature against the key it was built with before
it reads anything in the file, takes only a version later than its own, and checks any download
against the size and SHA-256 named there. It sends no account, key or device details. These are
signed with a preview key for proof-of-concept builds, separate from the release feed below.
Format and key: [docs/SIGNED-RELEASE-FILES.md](docs/SIGNED-RELEASE-FILES.md).

These files must not be edited by hand: any change, even to spacing, makes the signature fail.

## The release feed

[`release-feed.json`](release-feed.json) lists what is current for a ThoxAir: models today, and
provisioning artifacts (images, firmware, software) registered from the private provisioning bucket
`Thox-ai/thox-device-thoxair` as they are published. Each entry gives an address, an exact size and a SHA-256.

```
https://raw.githubusercontent.com/ttracx/thox-air-releases/main/release-feed.json
```

| Model | Version | Bytes | SHA-256 |
| --- | --- | --- | --- |
| ThoxAir 0.5B | 1.0.0 | 397807584 | `fb32e5ab802df466809836182f071bb0ab0871abb9273131456c89d998bccd6a` |

### Unsigned status

This feed is **unsigned**. No `release-feed.json.sig` is published for this repository yet.
Signing is pending signature by the holder of the THOX release key (`thox-release-2026-11`).
Until a signature is published and verified, consumers must not trust this feed as signed.
Format and the planned signature scheme: [docs/RELEASE-FEED.md](docs/RELEASE-FEED.md).

## Repository layout

- `feed.json` — the update list (`thoxair-update-feed/1`).
- `release-feed.json` — the release feed (`thoxair-release-feed/1`), unsigned pending signing.
- `<release line>/` — the signed `release.json` and `packages.json` a ThoxAir reads.
- `docs/` — format, user guide, quick start and development docs.
- `.agents/HANDOFF.md` — agent handoff.

## Documentation map

- [docs/USER_GUIDE.md](docs/USER_GUIDE.md)
- [docs/QUICKSTART.md](docs/QUICKSTART.md)
- [docs/FORMAT.md](docs/FORMAT.md)
- [docs/RELEASE-FEED.md](docs/RELEASE-FEED.md)
- [docs/SIGNED-RELEASE-FILES.md](docs/SIGNED-RELEASE-FILES.md)
- [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md)

## Releases

Formal releases are on the [Releases page](https://github.com/ttracx/thox-air-releases/releases).

## Agent handoff

See [.agents/HANDOFF.md](.agents/HANDOFF.md).

## Governance note

Public publishing (social, website, store listings, public repo flips, registries, campaigns)
requires Craig Ross's explicit approval via craig@thox.ai, CC tommy@thox.ai. This repository was
created public, list-only, on Tommy Xaypanya's CTO authority following the ThoxKey release-list
precedent (2026-11-10): versions, dates, links and checksums only, no code and no binaries.
Provisioning artifacts themselves live in the private bucket `Thox-ai/thox-device-thoxair`, internal access only.

## License and notice

Apache License 2.0, see [LICENSE](LICENSE). [NOTICE.md](NOTICE.md) carries the THOX.ai LLC notice.
