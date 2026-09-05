<div align="center">

# NodeFlow

### Industrial Visual Workflow Platform
### 工业可视化流程编排与执行平台

**Industrial Automation · Machine Vision · Device Integration · Runtime Orchestration**  
**工业自动化 · 机器视觉 · 设备集成 · 流程运行时**

<br/>

![Platform](https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=flat-square)
![UI](https://img.shields.io/badge/UI-Qt-41CD52?style=flat-square)
![Vision](https://img.shields.io/badge/Vision-OpenCV-5C3EE8?style=flat-square)
![Protocol](https://img.shields.io/badge/Protocol-Modbus%20%7C%20Serial%20%7C%20HTTP-555555?style=flat-square)
![Repository](https://img.shields.io/badge/Repository-Public%20Releases-181717?style=flat-square)

<br/>

[**简体中文**](#简体中文) · [**English**](#english) · [**Releases**](../../releases) · [**发布指南 / Release Guide**](docs/RELEASE-GUIDE.md)

</div>

---

# 简体中文

## 什么是 NodeFlow？

**NodeFlow** 是一套面向工业自动化、机器视觉与设备集成场景的**可视化流程编排与执行平台**。

它把传统程序中分散的采集、判断、图像处理、设备通信、流程控制与生产数据交互，组织成可以配置、组合、复用和扩展的节点工作流。

```text
设备 / 传感器 / 相机
        │
        ▼
   Trigger / Input
        │
        ▼
┌──────────────────────┐
│   NodeFlow Runtime   │
│   Graph / Workflow   │
└──────────────────────┘
        │
   ┌────┼────────────┐
   ▼    ▼            ▼
机器视觉  设备通信      数据 / MES
OpenCV   Modbus       HTTP
         Serial       Python
```

NodeFlow 的目标并不只是“画节点”，而是让节点图真正承担工业流程的**配置、执行、扩展与运行时调度**。

## 核心能力

| 能力 | 说明 |
| --- | --- |
| 🧩 **可视化流程编排** | 使用节点与连线组织工业逻辑和数据流 |
| ⚙️ **运行时执行** | 工作流不只是配置文件，可由 Runtime 实际调度执行 |
| 🔌 **插件化架构** | 设备、算法、协议和业务能力可以通过插件扩展 |
| 🔀 **类型化数据端口** | 支持不同数据类型、端口连接与运行时传播 |
| 💾 **工作流持久化** | Graph / Workflow 支持 JSON 保存与加载 |
| 🎯 **触发式流程** | 可由传感器、事件、协议数据等触发工作流 |
| 👁️ **机器视觉** | 集成 OpenCV，可扩展相机、检测与图像处理节点 |
| 🏭 **工业通信** | 支持 Modbus TCP / RTU、Serial 等通信能力 |
| 🌐 **系统集成** | 支持 HTTP、MES 与外部系统交互 |
| 🐍 **Python 扩展** | 可通过 Python 扩展算法和业务逻辑 |
| 🧱 **自定义设备插件** | 面向工业设备和现场协议进行独立扩展 |
| 🔄 **兼容性机制** | 面向插件版本、接口和数据结构持续演进 |

## 这个仓库是什么？

`nodeflow-releases` 是 **NodeFlow 的公开发布仓库**。

这里主要用于：

- 📦 Windows 安装包与便携版
- 📝 Release Notes / 版本说明
- 🔐 SHA-256 文件校验
- 📄 第三方依赖与许可证声明
- 🔗 提供给 ONEWU 软件中心和其他公开页面的下载地址

> **NodeFlow 主源码在独立仓库中维护，本仓库不公开主源码。**

## 下载

正式版本通过 GitHub **Releases** 发布：

➡️ **[前往 NodeFlow Releases](../../releases)**

推荐的发布资产命名：

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

大型二进制安装包应作为 **GitHub Release Assets** 上传，而不是长期提交进 Git 历史。

## 版本规则

NodeFlow 优先采用语义化版本风格：

```text
vMAJOR.MINOR.PATCH
```

例如：

```text
v0.1.0
v0.2.0
v0.2.1
```

预发布版本：

```text
v0.3.0-beta.1
v0.3.0-rc.1
```

## 文件完整性校验

每个正式发布包建议同时提供 `SHA256SUMS.txt`。

Windows PowerShell：

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

把输出结果与同一 Release 中的 `SHA256SUMS.txt` 对比即可。

## Qt 与第三方组件

NodeFlow 的 Windows 发布包可能包含 Qt Runtime、OpenCV 以及其他第三方运行时组件。

正式分发时应随包提供适用的许可证、版权声明和第三方归属信息，例如：

```text
licenses/
├─ Qt-LICENSE.txt
├─ LGPL-3.0.txt
└─ THIRD-PARTY-NOTICES.txt
```

NodeFlow 自身源码与第三方运行库分别管理；发布前请完成依赖与许可证检查。

详细流程见：**[发布指南](docs/RELEASE-GUIDE.md)**

---

# English

## What is NodeFlow?

**NodeFlow** is a **visual workflow orchestration and execution platform** built for industrial automation, machine vision, device connectivity and production-system integration.

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

Every official binary should be distributed with a SHA-256 checksum.

On Windows PowerShell:

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

Compare the result with `SHA256SUMS.txt` from the same release.

## Qt and third-party components

NodeFlow Windows packages may include Qt Runtime, OpenCV and other third-party runtime components.

Official distributions should include the applicable license texts, copyright notices and third-party attribution files, for example:

```text
licenses/
├─ Qt-LICENSE.txt
├─ LGPL-3.0.txt
└─ THIRD-PARTY-NOTICES.txt
```

NodeFlow's own source code and third-party runtime components are managed separately. Dependency and license checks should be completed before every public release.

See the **[Release Guide](docs/RELEASE-GUIDE.md)** for the publishing workflow.

---

<div align="center">

**NodeFlow** · Build industrial workflows as composable systems.

**NodeFlow** · 让工业流程成为可组合、可执行、可扩展的系统。

</div>
