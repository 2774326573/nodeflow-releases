# NodeFlow Release Guide

[简体中文](RELEASE-GUIDE.md) · [English](RELEASE-GUIDE.en.md)

This document defines the public binary release workflow for NodeFlow.

## 1. Release build

Build NodeFlow using a clean **Release** configuration and verify that the final package does not depend on local development directories, Qt SDK paths or temporary files.

For Windows Qt builds, dynamic linking is recommended, with the required Qt runtime libraries distributed alongside the application.

## 2. Recommended package layout

A typical portable package:

```text
NodeFlow/
├─ NodeFlow.exe
├─ plugins/
├─ platforms/
├─ imageformats/
├─ styles/
├─ licenses/
│  ├─ Qt-LICENSE.txt
│  ├─ LGPL-3.0.txt
│  └─ THIRD-PARTY-NOTICES.txt
└─ README.txt
```

Only ship runtime files actually required by the selected build and enabled plugins.

## 3. Qt deployment

Use the Qt deployment tool matching the Qt installation used to build NodeFlow, for example:

```powershell
windeployqt .\NodeFlow.exe
```

Inspect the generated package manually afterwards.

> `windeployqt` helps deploy runtime libraries but **does not replace a license audit**. When Qt WebEngine is enabled, Chromium, FFmpeg and other third-party components may require additional notices.

## 4. Third-party license audit

Before every public release, verify at least:

- Qt modules actually shipped
- Qt WebEngine / Chromium when enabled
- OpenCV
- Modbus-related components
- Python runtime / Python packages when bundled
- Camera or device-vendor SDKs
- Other third-party or proprietary runtimes distributed with NodeFlow

Update:

```text
THIRD-PARTY-NOTICES.txt
```

## 5. Formal asset naming

Existing v1.0.0 assets keep their current names to avoid breaking public URLs.

**Starting with subsequent releases, use formal product names:**

```text
NodeFlow-vX.Y.Z-Windows-x64-Qt-Portable.zip
NodeFlow-vX.Y.Z-Windows-x64-wxWidgets-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

If an installer is provided:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
```

Do not use new `nodeflow_demo-*` names for public release assets.

Large installers and ZIP archives should be uploaded as **GitHub Release Assets** rather than committed permanently into Git history.

## 6. SHA-256 checksums

PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Qt-Portable.zip -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-wxWidgets-Portable.zip -Algorithm SHA256
```

Record the results in:

```text
SHA256SUMS.txt
```

## 7. Versioning and compatibility

Recommended tags:

```text
v1.0.1
v1.1.0-beta.1
v1.1.0-rc.1
v2.0.0
```

Release title:

```text
NodeFlow vX.Y.Z
```

NodeFlow is now on a public `1.x` line, so the default policy is:

- `PATCH`: fixes without breaking public interfaces.
- `MINOR`: backward-compatible feature additions.
- `MAJOR`: may contain explicit breaking changes.

Within `1.x`, preserve compatibility wherever practical for:

- Workflow / Graph JSON
- Plugin ABI/API
- Port and data-type semantics
- Plugin Manifest / metadata structures
- Publicly observable runtime behavior

If a public boundary must break, document a migration path and prefer a new major version.

## 8. Release Notes template

```markdown
# NodeFlow vX.Y.Z

## Highlights
- ...

## Added
- ...

## Changed
- ...

## Fixed
- ...

## Compatibility
- Windows 10 / 11 x64
- Qt runtime: ...
- Plugin ABI/API: ...
- Workflow schema: ...

## Downloads
- Qt Portable
- wxWidgets Portable
- Setup (if available)

## Verification
See `SHA256SUMS.txt`.

## Known issues
- ...
```

## 9. latest.json

The repository root maintains:

```text
latest.json
```

It is the **machine-readable stable release manifest** consumed by ONEWU Software Center and other clients. It should contain at least:

- stable version / tag
- publish time
- recommended build
- Release URL
- platform asset URLs
- file sizes
- SHA-256 values
- third-party notices URL

After every Stable Release is published, `latest.json` must be updated.

Recommended flow:

```text
NodeFlow Build
      ↓
GitHub Release
      ↓
latest.json
      ↓
ONEWU Software Center
      ↓
User Download
```

## 10. Final release checklist

- [ ] Test on a clean Windows machine or VM
- [ ] Verify startup without a Qt SDK installed
- [ ] Verify plugin discovery and loading
- [ ] Run at least one representative workflow
- [ ] Test Modbus / Serial / Vision features included in the package
- [ ] Verify SHA-256 for every downloadable file
- [ ] Verify license and attribution files are present
- [ ] Update `latest.json`
- [ ] Document compatibility and breaking changes in Release Notes
- [ ] Confirm no source code, API keys, secrets, internal paths or private configuration files are included
