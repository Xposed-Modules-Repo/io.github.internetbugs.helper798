# 798 助手

「慧生活798」（`com.cloudora.android`）的去广告 LSPosed 模块。

开屏广告、横幅、信息流、激励视频、插屏、商城广告全部在请求层拦掉，宿主应用走「广告加载失败」的正常分支，所以不会出现空白框或转圈卡住；底栏的「积分」选项卡和「我的」页积分入口一并移除。

- 包名：`io.github.internetbugs.helper798`
- 当前版本：**1.4.0**（versionCode 10400）
- [下载模块 APK](https://github.com/Xposed-Modules-Repo/io.github.internetbugs.helper798/releases)
- [源码、构建说明与问题反馈](https://github.com/InternetBugs/798-helper)

## 效果

| 位置 | 原来 | 现在 |
| --- | --- | --- |
| 启动 App | 开屏广告，等几秒 | 直接进首页 |
| 首页 | 横幅广告、信息流广告 | 干净 |
| 积分任务 | 「看广告赚积分」入口 | 干净 |
| 各处弹窗 | 插屏、全屏广告 | 不再出现 |
| 商城页 | 商城广告 | 干净 |
| 底部导航 | 首页 / **积分** / 服务 / 我的 | 首页 / 服务 / 我的 |
| 「我的」页 | 钱包 / 卡包 / 卡券 / **积分** | 钱包 / 卡包 / 卡券 |

## 前提条件

- 手机已 root（KernelSU、Magisk 都行）
- 已安装 [LSPosed](https://github.com/LSPosed/LSPosed)
- 「慧生活798」版本 **3.1.10**，其他版本没测过，可能部分失效

## 安装

1. 到本仓库 [Releases](https://github.com/Xposed-Modules-Repo/io.github.internetbugs.helper798/releases) 下载 `798-helper.apk`
2. 安装它。**桌面和应用列表里不会出现图标，这是正常的**——它没有界面，是个后台模块
3. 打开 **LSPosed** → 底部「模块」→ 找到「**798 助手**」→ 打开右边开关
4. 点进「798 助手」，在作用域里勾选「**慧生活798**」
5. 强制停止「慧生活798」（设置 → 应用 → 慧生活798 → 强行停止），然后重新打开

第 5 步别省。模块只在目标应用启动时加载，不强制停止一次不会生效。

## 兼容性与验证范围

- 框架：LSPosed 2.2.1，libxposed 现代 API 102（`io.github.libxposed.api`）
- 模块 `minSdk 24` / `targetSdk 35`
- 目标应用只在 **慧生活798 3.1.10** 上实测过；应用更新后广告入口的类名可能变化，需要重新适配
- 作用域只有 `com.cloudora.android`，模块代码不在其他进程加载；不联网、不上报、不改登录状态和数据

## 常见问题

**LSPosed 的模块列表里找不到它**

先把列表下拉刷新一次。还是没有的话，确认装的是本仓库 Release 里的 apk，然后跑 `adb shell pm list packages | grep internetbugs`，能查到 `io.github.internetbugs.helper798` 就说明装上了。

**开关开了，广告还在**

九成是作用域没勾。LSPosed → 模块 → 798 助手，确认「慧生活798」那一项打勾，然后强制停止目标应用再打开。改完作用域不需要重启手机，但必须强制停止一次。

**会不会影响别的应用**

不会。作用域只有「慧生活798」一个包，模块代码只在这个进程里加载。

**安全吗，会不会封号**

模块只拦截广告请求，不改登录状态、不改数据、不联网、不上报任何东西。但任何修改客户端的行为都有风险，自己权衡。

## 源码与许可证

本仓库只用于模块介绍和 APK 分发，不放源码。完整源码、构建脚本与问题反馈见 [InternetBugs/798-helper](https://github.com/InternetBugs/798-helper)，许可证为 [MIT](LICENSE)。

仅供学习交流，请勿用于商业用途。使用本模块产生的任何后果由使用者自行承担。
