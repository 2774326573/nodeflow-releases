# NodeFlow Release Guide

This repository is the public binary distribution channel for NodeFlow.

## 1. Build

Build NodeFlow in a clean Release configuration and verify that the package does not depend on local development paths.

For Windows Qt builds, prefer dynamic linking and deploy the required Qt runtime libraries together with the application.

## 2. Package layout

A typical portable package should resemble:

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

Only include runtime files that are required by the selected NodeFlow build and enabled plugins.

## 3. Qt deployment

Use the Qt deployment tool appropriate for the Qt installation used to build NodeFlow, then inspect the result manually.

Example:

```powershell
windeployqt .\NodeFlow.exe
```

Do not treat the output of `windeployqt` as a complete license audit. Qt WebEngine, Chromium, FFmpeg and other third-party libraries can have additional notice requirements.

## 4. Third-party license audit

Before every public release, verify the licenses of all shipped dependencies, including at least:

- Qt modules actually shipped
- Qt WebEngine / Chromium when enabled
- OpenCV
- Modbus-related libraries
- Python runtime or Python packages when bundled
- Any camera/vendor SDK
- Any proprietary runtime redistributed with NodeFlow

Generate or update `THIRD-PARTY-NOTICES.txt` accordingly.

## 5. Create distribution files

Recommended files:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

Do not commit installers and large ZIP files directly to the repository unless there is a specific reason. Attach them to a GitHub Release.

## 6. Generate SHA-256 checksums

PowerShell example:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

Record the hashes in `SHA256SUMS.txt`.

## 7. Release naming

Use tags such as:

```text
v0.1.0
v0.2.0-beta.1
v0.3.0-rc.1
v1.0.0
```

Recommended release title:

```text
NodeFlow vX.Y.Z
```

## 8. Release notes template

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
See `SHA256SUMS.txt` attached to this release.

## Known issues
- ...
```

## 9. ONEWU integration

After a GitHub Release is published and verified, use the release asset URL as the public download source in ONEWU Software Center rather than linking to a file committed in the Git repository.

## 10. Final checks

Before marking a release stable:

- Test on a clean Windows machine or VM.
- Test startup without a Qt SDK installed.
- Test plugin discovery and loading.
- Test a representative workflow.
- Test Modbus / serial / vision functions included in the release.
- Verify every download hash.
- Verify license and attribution files are present.
- Confirm no source code, secrets, API keys, internal paths or private configuration files are included.
