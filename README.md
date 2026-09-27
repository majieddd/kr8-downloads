# kr8 downloads

This repository hosts **https://downloads.kr8.dev**, the download page and update feeds for kr8.
It holds no source code.

- `desktop/latest.json` is the Windows update feed that installed copies of kr8 read.
- `android/latest.json` is the Android update feed that the kr8 app reads.
- Installers and APKs are attached to this repository's GitHub Releases, one release per version:
  `desktop-vX.Y.Z` and `android-vX.Y.Z`.

Every desktop update is signed with kr8's updater key, and installed copies refuse an update whose
signature does not verify. Every APK is signed with kr8's release key. The SHA-256 of each file is
listed on the download page and in its feed.

Releases are produced by `scripts/kr8/release-desktop.mjs` and `mobile/scripts/` in the private
kr8 repository. Do not edit the feeds by hand.
