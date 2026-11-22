# Signed release files

Each release line has a folder:

| File | What it is |
| --- | --- |
| `release.json` | The current release for that line: version, notes, and the update file's name, exact size and SHA-256 |
| `release.json.sig` | Signature over the exact bytes of `release.json` |
| `packages.json` | The optional packages for that line: for each, version, file name, exact size and SHA-256 |
| `packages.json.sig` | Signature over the exact bytes of `packages.json` |

`release.json` uses schema `ai.thox.air-release.v1`; `packages.json` uses `ai.thox.air-packages.v1`.
In both, the field `board` holds the release line.

## The signature

ECDSA over the NIST P-256 curve with SHA-256. The `.sig` file is one line: the 64-byte signature
(`r` then `s`) in hexadecimal. A device holds only the public key and installs nothing that does
not verify.

| Key | Public key (uncompressed point, hexadecimal) |
| --- | --- |
| `thoxair-preview-2026-11` | `04e5b9711c2615fd3e29b12800eb44efc6cf9b4c638ef51c884a3cdc6e4a7d63514d7ca4766cfc9c36e5877ce3eb5927a1607766556fa55065b48ac0addde18bfc` |

This is a preview key for proof-of-concept builds. Product releases will be signed with a
different key, published here when it exists.

## What a device accepts

Only a file whose signature verifies; only a release for its own line; only a version later than
the one it runs. A listed version is then installed only if its file matches the signed size and
SHA-256. This address holds no files, so a device that reads it can tell that a later version
exists and will say that its files are not downloadable here.
