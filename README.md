<div align="center">

# NodeFlow

### 工业可视化流程编排与执行平台

**工业自动化 · 机器视觉 · 设备集成 · 流程运行时**

<br/>

![Platform](https://img.shields.io/badge/Platform-Windows%20x64-0078D4?style=flat-square)
![UI](https://img.shields.io/badge/UI-Qt-41CD52?style=flat-square)
![Vision](https://img.shields.io/badge/Vision-OpenCV-5C3EE8?style=flat-square)
![Protocol](https://img.shields.io/badge/Protocol-Modbus%20%7C%20Serial%20%7C%20HTTP-555555?style=flat-square)
![Repository](https://img.shields.io/badge/Repository-Public%20Releases-181717?style=flat-square)

<br/>

**简体中文** · [**English**](README.en.md) · [**Releases**](../../releases) · [**发布指南**](docs/RELEASE-GUIDE.md)

</div>

---

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

`nodeflow-releases` 是 **NodeFlow 的公开发布仓库**，主要用于：

- 📦 Windows 安装包与便携版
- 📝 Release Notes / 版本说明
- 🔐 SHA-256 文件校验
- 📄 第三方依赖与许可证声明
- 🔗 提供给 ONEWU 软件中心和其他公开页面的下载地址

> **NodeFlow 主源码在独立私有仓库中维护，本仓库不公开主源码。**

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

预发布版本例如：

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

NodeFlow 的 Windows 发布包可能包含 Qt Runtime、OpenCV 以及其他第三方运行时组件。正式分发时应随包提供适用的许可证、版权声明和第三方归属信息。

发布前请参阅：**[NodeFlow 发布指南](docs/RELEASE-GUIDE.md)**

---

<div align="center">

**NodeFlow · 让工业流程成为可组合、可执行、可扩展的系统。**

</div>
