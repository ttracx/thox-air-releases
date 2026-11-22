# Agent handoff — thox-air-releases

- Status: v1.0.0 published 2026-11-22. Public, list-only, mirroring ttracx/thox-key-releases.
- Key files: `feed.json` (`thoxair-update-feed/1`, channel `preview`: 1 release, 2 packages,
  1 image, all for line `air-nano`, proof of concept), `air-nano/release.json` and
  `packages.json` with `.sig` files (ECDSA P-256, preview key `thoxair-preview-2026-11`, made by
  `scripts/make-release-list.py` in ttracx/thoxair-poc; never edit by hand), `release-feed.json`
  (`thoxair-release-feed/1`, sequence 1, 1 model item(s): thoxair-0.5b).
- Conventions: verified values only, never invent url/bytes/sha256; bump sequence on feed
  changes; `release-feed.json` is `-text`, never convert line endings.
- Blockers: release feed is UNSIGNED — no release-feed.json.sig exists. Signing is pending the
  holder of Ed25519 key `thox-release-2026-11`; no private key or signing tool was found in the
  workspace or on KnightHub in the checked locations. Consumers must not trust the feed as signed.
- Bucket manifest: updated 2026-11-22 - manifest.json now records release_feed_repo and
  release_feed URLs for this repo; artifacts still [] (nothing added).
- Bucket: `Thox-ai/thox-device-thoxair` is private (internal only), placeholders only at creation
  (README.md, manifest.json with artifacts: [], .keep files). Registering this feed's repo URL
  in the bucket manifest is a recorded next step, not yet done.
- 2026-11-22, second lane (ThoxAir provisioning work in ttracx/thoxair-poc): 14 artifacts are now
  stored, read back and registered in the bucket manifest (update bundle, 2 packages, card image,
  vendor base, signed files, preview public key), source revision 119ae69. `feed.json` and
  `air-nano/` list them by size and SHA-256. They carry no download address: the files are
  private, so a device that reads this address learns a later version exists and no more.
  `release-feed.json` was left exactly as it was.
- Checked 2026-11-22: a ThoxAir bench device read `air-nano/release.json` and `packages.json` at this
  address over https and verified both signatures with the preview key; asked to install, it refused
  with a plain sentence, because the files are not here.
- Next: sign the release feed; decide whether update files get a public address (Tommy's call);
  replace the preview key with a production key before any product release.
- Last verified: 2026-11-22 by Sadie (subagent lane, device release feeds).
