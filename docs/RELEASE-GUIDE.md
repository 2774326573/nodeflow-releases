# NodeFlow Release Guide / 发布指南

[简体中文](#简体中文) · [English](#english)

---

# 简体中文

本文档用于规范 NodeFlow 的公开二进制发布流程。

## 1. Release 构建

使用干净的 **Release** 配置构建 NodeFlow，并确认最终程序不依赖本机开发目录、Qt SDK 路径或临时文件。

Windows Qt 版本建议使用**动态链接**，并随应用一起部署所需 Qt Runtime。

## 2. 推荐目录结构

典型便携版可以采用：

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

只携带当前构建和启用插件真正需要的运行时文件。

## 3. Qt 部署

使用与 NodeFlow 编译环境相匹配的 Qt 部署工具，例如：

```powershell
windeployqt .\NodeFlow.exe
```

完成后仍需人工检查输出。

> `windeployqt` 只能帮助部署运行库，**不能替代许可证审计**。如果启用了 Qt WebEngine，还需要关注 Chromium、FFmpeg 等第三方组件的声明要求。

## 4. 第三方许可证审计

每次公开发布前至少检查：

- 实际随包发布的 Qt 模块
- Qt WebEngine / Chromium（如启用）
- OpenCV
- Modbus 相关组件
- Python Runtime / Python packages（如随包）
- 相机或设备厂商 SDK
- 其他随 NodeFlow 分发的第三方或专有运行库

并更新：

```text
THIRD-PARTY-NOTICES.txt
```

## 5. 发布文件命名

推荐：

```text
NodeFlow-vX.Y.Z-Windows-x64-Setup.exe
NodeFlow-vX.Y.Z-Windows-x64-Portable.zip
SHA256SUMS.txt
THIRD-PARTY-NOTICES.txt
```

大型安装包和 ZIP 应作为 **GitHub Release Assets** 上传，不要长期直接提交进 Git 历史。

## 6. SHA-256 校验

PowerShell：

```powershell
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Setup.exe -Algorithm SHA256
Get-FileHash .\NodeFlow-vX.Y.Z-Windows-x64-Portable.zip -Algorithm SHA256
```

把结果写入：

```text
SHA256SUMS.txt
```

## 7. 版本命名

推荐 Tag：

```text
v0.1.0
v0.2.0-beta.1
v0.3.0-rc.1
v1.0.0
```

Release 标题：

```text
NodeFlow vX.Y.Z
```

## 8. Release Notes 模板

```markdown
# NodeFlow vX.Y.Z

## Highlights / 重点
- ...

## Added / 新增
- ...

## Changed / 变更
- ...

## Fixed / 修复
- ...

## Compatibility / 兼容性
- Windows 10 / 11 x64
- Qt runtime: ...
- Plugin ABI/API: ...

## Downloads / 下载
- Setup installer
- Portable ZIP

## Verification / 校验
See / 参见 `SHA256SUMS.txt`.

## Known issues / 已知问题
- ...
```

## 9. ONEWU 软件中心接入

GitHub Release 发布并验证完成后，ONEWU Software Center 应保存对应 **Release Asset URL** 作为公开下载地址，而不是链接仓库中的普通 Git 文件。

推荐链路：

```text
NodeFlow Build
      ↓
GitHub Release
      ↓
Release Asset URL
      ↓
ONEWU Software Center
      ↓
用户下载
```

## 10. 正式发布前检查

- [ ] 在干净 Windows 机器或虚拟机运行测试
- [ ] 未安装 Qt SDK 时可正常启动
- [ ] 插件可发现并加载
- [ ] 至少运行一套代表性 Workflow
- [ ] 测试当前发布包包含的 Modbus / Serial / Vision 功能
- [ ] 校验所有下载文件 SHA-256
- [ ] 确认许可证和第三方声明存在
- [ ] 确认没有源码、API Key、Secret、内部路径或私有配置泄漏

---

# English

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

## Highlights / 重点
- ...

## Added / 新增
- ...

## Changed / 变更
- ...

## Fixed / 修复
- ...

## Compatibility / 兼容性
- Windows 10 / 11 x64
- Qt runtime: ...
- Plugin ABI/API: ...

## Downloads / 下载
- Setup installer
- Portable ZIP

## Verification / 校验
See / 参见 `SHA256SUMS.txt`.

## Known issues / 已知问题
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
