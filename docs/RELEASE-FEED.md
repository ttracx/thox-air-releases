# Release feed (`thoxair-release-feed/1`) — unsigned

One JSON object in `release-feed.json`. There is **no** `release-feed.json.sig` for this
repository yet: the feed is unsigned pending signature by the holder of the THOX release key.
Consumers must not trust this feed as signed until a signature is published and verified.

```json
{"schema":"thoxair-release-feed/1","channel":"stable","sequence":1,"published":"2026-11-22",
 "items":[
  {"kind":"model","id":"thoxair-0.5b","version":"1.0.0","title":"ThoxAir 0.5B","host":"any",
   "url":"https://huggingface.co/Thox-ai/ThoxAir-0.5B/resolve/5a79699fbdafbeb9232628cd8e3aa5a4ba918b36/ThoxAir-0.5B.Q4_K_M.gguf",
   "bytes":397807584,"sha256":"fb32e5ab802df466809836182f071bb0ab0871abb9273131456c89d998bccd6a","bucket":"Thox-ai/thox-device-thoxair","notes":"..."}]}
```

| Field | Meaning |
| --- | --- |
| `sequence` | Goes up with every published feed. An app should refuse a feed with a lower number than one it has accepted |
| `kind` | `setup`, `start`, `image`, `model`, `firmware`, `software` or `package` |
| `id` | Lower-case letters, digits, `.`, `_`, `-` |
| `version` | `major.minor.patch`, optionally `-pre` and `+build`; a prerelease sorts before its release |
| `host` | `any`, `windows`, `macos` or `linux` |
| `url` | `https://` on `huggingface.co`, `github.com`, `raw.githubusercontent.com` or `registry.ollama.ai` |
| `bytes`, `sha256` | The exact size and SHA-256 of the file |
| `bucket` | The private THOX provisioning bucket the item is registered from (internal access only) |
| `files` | For a package, its files; for an image, its parts in order: `path`, `url`, `bytes`, `sha256` |

Provisioning artifacts (images, firmware, software) will be registered from the private bucket
`Thox-ai/thox-device-thoxair` as they are published. No image or firmware items are listed yet, because none are
published in that bucket yet.

## The planned signature

When signed, the signature will follow the ThoxKey release-feed scheme:

```json
{"alg":"ed25519","keyId":"thox-release-2026-11","signature":"<base64>"}
```

The signature covers the exact bytes of `release-feed.json`. The public key published for the
ThoxKey feed is:

| Key id | Public key (base64) |
| --- | --- |
| `thox-release-2026-11` | `vKkaFljVSPmbIyJ5RhLoZpZdvbVVADQlUAZDKslH/VY=` |

No signature file exists for this feed yet, so the key above does not yet authenticate it.

## Check a download yourself

```sh
curl -fsSL https://raw.githubusercontent.com/ttracx/thox-air-releases/main/release-feed.json -o release-feed.json
shasum -a 256 <downloaded-file>
```

The second line must print the `sha256` the feed lists for that file.
