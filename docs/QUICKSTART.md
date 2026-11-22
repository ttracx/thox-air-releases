# Quick start

Five minutes, read-only:

```sh
# The update list (proof-of-concept entries, preview channel)
curl -fsSL https://raw.githubusercontent.com/ttracx/thox-air-releases/main/feed.json

# The release feed (models current for ThoxAir)
curl -fsSL https://raw.githubusercontent.com/ttracx/thox-air-releases/main/release-feed.json

# Verify a downloaded model against the feed
shasum -a 256 <downloaded-file>
```

Compare the printed SHA-256 with the entry in `release-feed.json`. Full guide:
[USER_GUIDE.md](USER_GUIDE.md). Formats: [FORMAT.md](FORMAT.md),
[RELEASE-FEED.md](RELEASE-FEED.md),
[SIGNED-RELEASE-FILES.md](SIGNED-RELEASE-FILES.md).
