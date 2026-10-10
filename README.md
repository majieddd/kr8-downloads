# kr8 downloads

This repository hosts **https://downloads.kr8.app**, the download page and update feeds for kr8.
It holds no source code.

- `desktop/latest.json` is the Windows update feed that installed copies of kr8 read.
- `android/latest.json` is the Android update feed that the kr8 app reads.
- Installers and APKs are attached to this repository's GitHub Releases, one release per version:
  `desktop-vX.Y.Z` and `android-vX.Y.Z`.

The site used to be **https://downloads.kr8.dev**. That name now forwards here (a redirect on the
kr8.dev Cloudflare zone), because Windows 0.4.4 and earlier and Android 0.4.2 and earlier read their
feeds only there. Later versions ask downloads.kr8.app first and downloads.kr8.dev second. Keep the
forwarding until installs have moved (see `docs/kr8/session7/KR8-APP-MIGRATION.md` in the kr8
repository).

Every desktop update is signed with kr8's updater key, and installed copies refuse an update whose
signature does not verify. Every APK is signed with kr8's release key. The SHA-256 of each file is
listed on the download page and in its feed.

Releases are produced by `scripts/kr8/release-desktop.mjs` and `mobile/scripts/` in the private
kr8 repository. Do not edit the feeds by hand.

`assets/android-qr.svg` is generated with segno 1.6.6 (installed in `C:/kr8-build/tools/py`). Run
this from this folder; it writes through a byte buffer so the file keeps LF line endings on Windows:

```
python -c "import io, segno; b = io.BytesIO(); segno.make('https://downloads.kr8.app/#android').save(b, kind='svg', scale=6, border=2, dark='#141625', light='#fff'); open('assets/android-qr.svg', 'wb').write(b.getvalue())"
```
