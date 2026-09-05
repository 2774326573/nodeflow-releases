# NodeFlow Release Guide

[简体中文](RELEASE-GUIDE.md) · **English**

This document defines the public binary release workflow for NodeFlow.

## 1. Release build

Build NodeFlow using a clean **Release** configuration and verify that the final package does not depend on local development directories, Qt SDK paths or temporary files.

For Windows Qt builds, dynamic linking is recommended, with the required Qt runtime libraries distributed alongside the application.

## 2. Recommended package layout

A typical portable package may look like:

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

Before every public release, verify the licenses of at least:

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

## 5. Distribution file names

Recommended:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

Large installers and ZIP archives should be uploaded as **GitHub Release Assets** rather than committed permanently into Git history.

## 6. SHA-256 checksums

PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

Record the results in:

```text
SHA256SUMS.txt
```

## 7. Version naming

Recommended tags:

```text
v0.1.0
v0.2.0-beta.1
v0.3.0-rc.1
v1.0.0
```

Release title:

```text
NodeFlow vX.Y.Z
```

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

## Downloads
- Setup installer
- Portable ZIP

## Verification
See `SHA256SUMS.txt`.

## Known issues
- ...
```

## 9. ONEWU Software Center integration

After a GitHub Release has been published and verified, ONEWU Software Center should use the corresponding **Release Asset URL** as its public download source rather than linking to ordinary files committed to Git.

Recommended flow:

```text
NodeFlow Build
      ↓
GitHub Release
      ↓
Release Asset URL
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
- [ ] Confirm no source code, API keys, secrets, internal paths or private configuration files are included
