# Dora Translator PC — Updates

This repo hosts the update manifest and release binaries for Dora Translator PC.

The app checks `dora-update.json` on launch. When a new version is available,
the user clicks **Cập nhật ngay** and the app downloads the installer, runs it
silently, and relaunches.

## Publishing a new version

1. Build the installer (see the source repo's `build.ps1` or Docker command).
2. Create a GitHub Release here with tag `v<version>` (e.g. `v1.3.8`).
3. Upload `DoraTranslator-PC-<version>-Setup.exe` as a release asset.
4. Update `dora-update.json`:

```json
{
  "schemaVersion": 1,
  "release": {
    "version": "1.3.8",
    "build": 46,
    "minimumWindows": "10.0.19041",
    "notes": "What changed.",
    "downloadURL": "https://github.com/meownbb/dora-translator-pc/releases/download/v1.3.8/DoraTranslator-PC-1.3.8-Setup.exe"
  }
}
```

5. Commit and push. Users see the update on next app launch.

Optional manifest fields: `notice`, `minBuild`, `blockMessage`, `blockURL`.
