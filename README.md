# NodeFlow Releases

> Visual workflow platform for industrial automation, machine vision and device integration.

**NodeFlow** is a visual workflow execution platform designed for industrial automation, machine vision, device communication and production-system integration.

NodeFlow turns traditional code-driven workflows such as acquisition, inspection, decision making, device control and production-data exchange into configurable, composable and reusable node graphs.

## What this repository contains

This repository is the **public release channel** for NodeFlow. It is intended for:

- Windows installers and portable packages
- Release notes and version history
- SHA-256 checksums
- Runtime dependency and license notices
- Public download links used by ONEWU

The main NodeFlow source code is maintained separately and is **not published in this repository**.

## Core capabilities

- Visual node-based workflow orchestration
- Plugin-based architecture
- JSON workflow save/load
- Typed data ports and runtime data-flow execution
- Event / sensor triggered workflows
- Modbus TCP / RTU integration
- Serial communication
- HTTP / MES integration
- OpenCV-based machine vision processing
- Python extension support
- Custom industrial-device plugins
- Plugin versioning and compatibility mechanisms

## Recommended release assets

Each public version should normally provide:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

Binary packages should be attached to **GitHub Releases** rather than committed directly into Git history.

## Versioning

NodeFlow releases use semantic-style version numbers where practical:

```text
vMAJOR.MINOR.PATCH
```

Examples:

```text
v0.1.0
v0.2.0
v0.2.1
```

Pre-release builds may use suffixes such as:

```text
v0.3.0-beta.1
v0.3.0-rc.1
```

## Integrity verification

Every downloadable binary should have a SHA-256 checksum. On Windows PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

Compare the result with the `SHA256SUMS.txt` file attached to the same release.

## Qt and third-party components

NodeFlow may include Qt runtime libraries and other third-party components. The distributed package should include the applicable license notices and third-party attribution files. NodeFlow's own source code is not made public merely because the runtime package contains dynamically linked Qt libraries.

See [`docs/RELEASE-GUIDE.md`](docs/RELEASE-GUIDE.md) before publishing a new version.

---

## 中文说明

NodeFlow 是一套面向**工业自动化、机器视觉与设备集成**的可视化流程编排与执行平台。

这个仓库仅用于发布 NodeFlow 的公开安装包、便携版、版本说明、校验文件和第三方许可证声明。NodeFlow 主源码在独立私有仓库中维护，不在这里公开。

推荐每个版本通过 **GitHub Releases** 发布二进制文件，不要把大型安装包长期直接提交到 Git 历史中。
