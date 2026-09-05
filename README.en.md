<div align="center">

# NodeFlow

### Industrial Visual Workflow Platform

**Industrial Automation · Machine Vision · Device Integration · Runtime Orchestration**

<br/>

![Platform](https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=flat-square)
![UI](https://img.shields.io/badge/UI-Qt-41CD52?style=flat-square)
![Vision](https://img.shields.io/badge/Vision-OpenCV-5C3EE8?style=flat-square)
![Protocol](https://img.shields.io/badge/Protocol-Modbus%20%7C%20Serial%20%7C%20HTTP-555555?style=flat-square)
![Repository](https://img.shields.io/badge/Repository-Public%20Releases-181717?style=flat-square)

<br/>

[**简体中文**](README.md) · **English** · [**Releases**](../../releases) · [**Release Guide**](docs/RELEASE-GUIDE.en.md)

</div>

---

## What is NodeFlow?

**NodeFlow** is a visual workflow orchestration and execution platform for industrial automation, machine vision, device connectivity and production-system integration.

It turns traditionally code-driven acquisition, inspection, decision, device-control and production-data tasks into configurable, composable and reusable node graphs.

```text
Devices / Sensors / Cameras
            │
            ▼
       Trigger / Input
            │
            ▼
┌──────────────────────────┐
│      NodeFlow Runtime    │
│      Graph / Workflow    │
└──────────────────────────┘
            │
      ┌─────┼──────────────┐
      ▼     ▼              ▼
   Vision  Device         Data / MES
   OpenCV  Modbus         HTTP
           Serial         Python
```

NodeFlow is not intended to be only a node editor. Its goal is to make visual graphs responsible for real industrial **configuration, execution, extensibility and runtime orchestration**.

## Core capabilities

| Capability | Description |
| --- | --- |
| 🧩 **Visual workflow orchestration** | Build industrial logic and data flow with nodes and connections |
| ⚙️ **Runtime execution** | Graphs are executable workflows rather than static configuration only |
| 🔌 **Plugin architecture** | Extend devices, algorithms, protocols and business capabilities independently |
| 🔀 **Typed data ports** | Typed connections and runtime data propagation |
| 💾 **Workflow persistence** | Save and load Graph / Workflow definitions using JSON |
| 🎯 **Event-driven execution** | Trigger workflows from sensors, events and protocol data |
| 👁️ **Machine vision** | OpenCV integration with extensible camera and vision-processing nodes |
| 🏭 **Industrial communication** | Modbus TCP / RTU, Serial and other device communication capabilities |
| 🌐 **System integration** | HTTP, MES and external-system connectivity |
| 🐍 **Python extensions** | Extend algorithms and business logic with Python |
| 🧱 **Custom device plugins** | Integrate industrial devices and site-specific protocols |
| 🔄 **Compatibility mechanisms** | Designed for evolving plugin versions, interfaces and data structures |

## About this repository

`nodeflow-releases` is the **public distribution repository** for NodeFlow.

It is used for:

- 📦 Windows installers and portable packages
- 📝 Release notes and version history
- 🔐 SHA-256 checksums
- 📄 Runtime dependency and license notices
- 🔗 Public download URLs consumed by ONEWU and other distribution pages

> **The main NodeFlow source code is maintained separately and is not published in this repository.**

## Downloads

Official binaries are distributed through GitHub **Releases**:

➡️ **[Open NodeFlow Releases](../../releases)**

Recommended asset names:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

Large binaries should be attached as **GitHub Release Assets** instead of being committed permanently into Git history.

## Versioning

NodeFlow uses semantic-style versions where practical:

```text
vMAJOR.MINOR.PATCH
```

Pre-release examples:

```text
v0.3.0-beta.1
v0.3.0-rc.1
```

## Integrity verification

Every official binary should be distributed with a SHA-256 checksum.

On Windows PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

Compare the result with `SHA256SUMS.txt` from the same release.

## Qt and third-party components

NodeFlow Windows packages may include Qt Runtime, OpenCV and other third-party runtime components. Official distributions should include applicable license texts, copyright notices and third-party attribution files.

See the **[Release Guide](docs/RELEASE-GUIDE.en.md)** before publishing a version.

---

<div align="center">

**NodeFlow · Build industrial workflows as composable systems.**

</div>
