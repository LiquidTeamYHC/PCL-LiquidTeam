# PCL-LiquidTeam修改版

> **本仓库是第三方基于 [Plain Craft Launcher (PCL)](https://github.com/Meloong-Git/PCL) 独立修改的产物，非官方发布。**
>
> - 修改者：LiquidTeam
> - 上游版本：PCL 2.99.0.0（Release 413）
> - 授权：继续使用上游的 [LICENCE](LICENCE)（《PCL 分发有限许可》与《PCL 存储库合理使用指南》）
> - 原作者：龙腾猫跃 —— [赞助 PCL](https://meloong.com/afd/a/LTCat)

## 本修改版做了什么

上游自 2.99.0.0 起，因合规原因以编译期常量关闭了 Minecraft 下载功能。本版仅恢复该功能，其余与上游保持一致：

| 文件 | 改动 |
|---|---|
| `Plain Craft Launcher 2/Modules/ModSecret.vb` | `RestrictMcDownload` 由 `True` 改为 `False`（安装页、整合包、下载页卡片、Modpack 详情等处共用此常量） |
| `Plain Craft Launcher 2/Modules/Base/ModBase.vb` | `VersionDisplay` 追加 `PCL-LiquidTeam修改版` 后缀 |
| `Plain Craft Launcher 2/FormMain.xaml.vb` | 首次启动说明改为第三方版本说明（仅弹一次）；移除更新日志中与恢复下载相矛盾的条目 |
| `Plain Craft Launcher 2/Pages/PageOther/PageOtherAbout.xaml`、`My Project/AssemblyInfo.vb` | 名称与关于页标注为 `PCL-LiquidTeam修改版` |
| `MeloongCore/` | 上游以子模块引用，本仓库直接内联源码，克隆后可直接构建 |

## 构建

需要 Visual Studio（含 .NET Framework 4.8 开发工具）与 .NET SDK：

```bash
dotnet restore PCLCS/PCLCS.csproj
msbuild "Plain Craft Launcher 2/Plain Craft Launcher 2.vbproj" -p:Configuration=Release
```

产物：`Plain Craft Launcher 2/bin/Plain Craft Launcher 2.exe`（单文件，约 5.9 MB）。

## 已知限制

本版基于 PCL 的开源部分构建，因此不具备以下功能（首次启动会提示）：

- 启动器自动更新与联网公告
- 联机、主题切换、百宝箱
- 正版（Microsoft）登录：需自行通过环境变量 `PCL_MS_CLIENT_ID` 配置
- CurseForge 资源下载：需自行通过环境变量 `PCL_CURSEFORGE_API_KEY` 配置（Modrinth 等来源不受影响）

## 上游资源

- [PCL 下载](https://meloong.com/pcl)
- [PCL 功能投票](https://github.com/Meloong-Git/PCL/discussions/2)
- [帮助文档库](https://github.com/LTCatt/PCL2Help)
