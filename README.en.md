<div align="center">

# NodeFlow

### Industrial Visual Workflow Platform

**Industrial Automation · Machine Vision · Device Integration · Runtime Orchestration**

<br/>

![Platform](https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=flat-square)
![UI](https://img.shields.io/badge/UI-Qt-41CD52?style=flat-square)
![Vision](https://img.shields.io/badge/Vision-OpenCV-5C3EE8?style=flat-square)
![Protocol](https://img.shields.io/badge/Protocol-Modbus%20%7C%20Serial%20%7C%20HTTP-555555?style=flat-square)
![Release](https://img.shields.io/badge/Latest-v1.0.0-2ea44f?style=flat-square)

<br/>

[**简体中文**](README.md) · **English** · [**Releases**](../../releases) · [**Release Guide**](docs/RELEASE-GUIDE.en.md)

</div>

---

## Latest Release · NodeFlow v1.0.0

The first public Windows x64 binary release is now available.

| Build | Recommendation | Description | Download |
| --- | :---: | --- | --- |
| **Qt build** | ⭐ **Default** | Primary GUI build, portable and ready to run after extraction | [Download Qt build](https://github.com/2774326573/nodeflow-releases/releases/download/v1.0.0/nodeflow_demo-1.0.0-win64-qt.zip) |
| **MSVC / wxWidgets build** | Compatibility build | Portable package; WebView2 Runtime is provided by the target system | [Download MSVC build](https://github.com/2774326573/nodeflow-releases/releases/download/v1.0.0/nodeflow_demo-1.0.0-win64-msvc.zip) |

> **Not sure which one to use? Choose the Qt build.**

Supporting files:

- [SHA256SUMS.txt](https://github.com/2774326573/nodeflow-releases/releases/download/v1.0.0/SHA256SUMS.txt)
- [THIRD-PARTY-NOTICES.txt](https://github.com/2774326573/nodeflow-releases/releases/download/v1.0.0/THIRD-PARTY-NOTICES.txt)
- [Full Release Notes](https://github.com/2774326573/nodeflow-releases/releases/tag/v1.0.0)
- [Machine-readable latest release manifest](latest.json)

> Existing v1.0.0 asset names are intentionally preserved to avoid breaking public download URLs. **Future releases use formal NodeFlow asset names** instead of the `nodeflow_demo` prefix.

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

## Release asset naming

Starting with releases after v1.0.0, use formal product names:

```text
NodeFlow-vX.Y.Z-Windows-x64-Qt-Portable.zip
NodeFlow-vX.Y.Z-Windows-x64-wxWidgets-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

If an installer is provided later:

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
```

Large binaries are distributed as **GitHub Release Assets** and should not be committed directly into Git history.

## Versioning and compatibility

NodeFlow uses semantic-style versions:

```text
vMAJOR.MINOR.PATCH
```

The `1.x` line should preserve backward compatibility for published workflows, graph schemas, plugin interfaces and runtime behavior wherever practical. Clearly breaking changes should move to a new major version.

Pre-release examples:

```text
v1.1.0-beta.1
v1.1.0-rc.1
```

## Integrity verification

On Windows PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Qt-Portable.zip -Algorithm SHA256
```

Compare the result with `SHA256SUMS.txt` from the same release.

## Qt and third-party components

NodeFlow Windows packages may include Qt Runtime, OpenCV and other third-party runtime components. Official distributions should include applicable license texts, copyright notices and third-party attribution files.

See the **[Release Guide](docs/RELEASE-GUIDE.en.md)** before publishing a version.

---

<div align="center">

**NodeFlow · Build industrial workflows as composable systems.**

</div>
