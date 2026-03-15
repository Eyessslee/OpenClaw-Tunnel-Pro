<h1 align="center">OpenClaw Tunnel Pro 🚀</h1>

## 🖥️ 界面截图

### MacOS 版本
<p align="center">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/mac-image1.png" width="30%" alt="MacOS 演示图1">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/mac-image2.png" width="30%" alt="MacOS 演示图2">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/mac-image3.png" width="30%" alt="MacOS 演示图3">
</p>

### Win 版本
<p align="center">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/win-image1.png" width="30%" alt="Win 演示图1">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/win-image2.png" width="30%" alt="Win 演示图2">
  <img src="https://raw.githubusercontent.com/Eyessslee/OpenClaw-Tunnel-Pro/main/images/win-image3.png" width="30%" alt="Win 演示图3">
</p>

<p align="center">
<a href="#introduction-cn">中文说明</a> |
<a href="#introduction-en">English</a>
</p>

<h2 id="introduction-cn">介绍 (Introduction)</h2>

最近开发的一个小工具：OpenClaw Tunnel Pro。

最初开发这个工具是为了解决自己在管理 OpenClaw 实例时，频繁切换 SSH 隧道和查看实时指标的痛点。我希望它既能提供原生应用的丝滑体验，又能保障服务器凭据的存储安全。现在项目已经迭代到了 v3.5.2 版本，各项功能已趋于稳定，因此分享出来给有同样需求的朋友使用。

🌟 核心功能

实时数据闭环：直接通过 SSH 通道轮询 CLI 指令，实时抓取并汇总 Token 消耗（支持 24 小时增量过滤）、活跃连接数和接口请求总量。

系统级安全存储：所有服务器地址、用户名及密码均通过 macOS 的 Keychain 或系统级加密接口进行存储，本地不保留任何明文配置文件。

自动化连接管理：支持多节点配置快速切换，并内置自动分配逻辑以避让本地端口冲突；集成毫秒级心跳监测，断线自动重连。

原生交互美学：macOS 版深度适配系统级物理动效，支持监控面板的阶梯式进场动画；Windows 版支持原生 Mica (云母) 半透明效果。

🛠️ 技术实现要点

数据传输纠错：在 macOS 端的 SSH 指令中引入 -T 参数以禁用远程伪终端（PTY）机制，彻底解决了长 JSON 数据流因 Linux 终端强制自动换行（\r\n）而导致解析失效的问题。

环境自适应：支持 OpenClaw CLI 的绝对路径调用（如 /root/.nvm/.../bin/openclaw），规避了非交互式 SSH 环境下环境变量丢失的顽疾。

高性能渲染：在 macOS 上采用原生 NSImageView 引擎加载 GIF 素材，绕过 WebKit 沙盒对本地文件访问的限制，并解决大尺寸素材溢出问题。

内存级隧道操作：Windows 版利用 Rust 的 ssh2 库在内存中直接建立隧道映射，显著降低了系统资源占用。

💾 安装与运行说明

下载安装包：从仓库右侧的 Releases 页面下载最新的 .dmg (macOS) 或 .exe (Windows) 文件。

macOS 安全提示：由于应用未经过 Apple 开发者签名，初次打开时系统会提示“无法验证开发者”。

解决办法：在“访达 (Finder)”中找到应用，右键点击并选择“打开”，在弹出的窗口中再次点击“打开”即可。


📜 版本更新 (Changelog)

[v3.5.2]

引入 -T 参数禁用远程 PTY，修复超长数据截断问题；增加官方绝对路径支持；改用原生 NSImageView 渲染引擎。

[v3.5.1]

引入 Flexbox 约束修正 Windows 按钮对齐；启动时强制重置节点激活态，修复 UI 幽灵状态；物理级抹除 Windows 输入框白框。

[v3.5.0]

接入官方 CLI 统计，实现实时 Token、Links、Reqs 监测；新增作者信息模块与 GIF 动画支持；适配 macOS 26.0+ 高级动效。

[v1.0.0 - v3.0.0]

完成基础 SSH 隧道建立、多节点持久化管理、确立“孔雀蓝”视觉规范及全面接入系统级加密存储。

👨‍💻 关于作者 (About Author)

@Eyesslee

开发这个工具的初衷是追求视觉美感与底层技术的平衡。希望它能帮你从繁琐的运维指令中解脱出来，让隧道管理和实例监控变得更加简单、直观。

⚖️ 免责声明 (Disclaimer)

本项目及相关编译产物（App）仅供个人技术测试、交流与娱乐使用。

请勿将本工具用于任何非法用途或生产环境。

开发者不对因使用本工具导致的任何数据丢失、安全问题或系统故障承担法律责任。

本项目遵循 MIT 开源协议。

<h2 id="introduction-en">🇺🇸 English Introduction</h2>

Hello! I’d like to share a small utility I’ve been working on: OpenClaw Tunnel Pro.

I originally developed this tool to solve my own pain points—frequently switching SSH tunnels and checking real-time metrics while managing OpenClaw instances. My goal was to build a solution that combines the smooth experience of a native app with robust security for server credentials. Now at v3.5.2, the project has stabilized, so I’m sharing it with friends who have similar needs.

🌟 Core Features

- **Real-time Data Loop**: Directly polls CLI commands via SSH tunnels to capture and aggregate Token consumption (supports 24-hour incremental filtering), active connection counts, and total interface request volume in real time.
- **System-Level Secure Storage**: All server addresses, usernames, and passwords are stored via macOS Keychain or system-level encryption interfaces—no plaintext configuration files are kept locally.
- **Automated Connection Management**: Supports quick switching between multi-node configurations with built-in automatic allocation logic to avoid local port conflicts; integrates millisecond-level heartbeat monitoring for automatic reconnection on disconnection.
- **Native Interactive Aesthetics**: The macOS version deeply adapts to system-level physical animations, supporting a stepped entrance animation for the monitoring panel; the Windows version supports native Mica (mica) translucent effects.

🛠️ Technical Highlights

- **Data Transmission Error Correction**: Introduced the -T parameter in macOS SSH commands to disable the remote pseudo-terminal (PTY) mechanism, completely solving the problem of long JSON data streams failing to parse due to forced automatic line wrapping (\r\n) by Linux terminals.
- **Environment Adaptation**: Supports absolute path invocation of the OpenClaw CLI (e.g., /root/.nvm/.../bin/openclaw), avoiding the persistent issue of missing environment variables in non-interactive SSH environments.
- **High-Performance Rendering**: Uses the native NSImageView engine on macOS to load GIF assets, bypassing WebKit sandbox restrictions on local file access and solving the problem of large asset overflow.
- **Memory-Level Tunneling**: The Windows version leverages Rust’s ssh2 library to establish tunnel mappings directly in memory, significantly reducing system resource usage.

💾 Installation & Usage

- **Download Installer**: Get the latest .dmg (macOS) or .exe (Windows) file from the Releases section on the right side of the repository.
- **macOS Security Note**: Since the app is not signed with an Apple Developer ID, you may see a "cannot verify the developer" warning when opening it for the first time.
- **Solution**: Locate the app in Finder, right-click and select "Open", then click "Open" again in the pop-up window.


📜 Changelog (EN)

[v3.5.2]
- Introduced the -T parameter to disable remote PTY, fixing the issue of truncated long data; added support for official absolute paths; switched to the native NSImageView rendering engine.

[v3.5.1]
- Introduced Flexbox constraints to correct Windows button alignment; forced reset of node activation state on startup to fix UI ghost states; physically erased the white border of Windows input boxes.

[v3.5.0]
- Integrated official CLI statistics to achieve real-time Token, Links, and Reqs monitoring; added an author information module and GIF animation support; adapted to advanced animations for macOS 26.0+.

[v1.0.0 - v3.0.0]
- Completed basic SSH tunnel establishment, multi-node persistent management, established the "Peacock Blue" visual specification, and fully integrated system-level encrypted storage.

👨‍💻 About Author

@Eyesslee

The original intention behind developing this tool was to pursue a balance between visual aesthetics and underlying technology. I hope it helps you free yourself from tedious operation and maintenance commands, making tunnel management and instance monitoring simpler and more intuitive.

⚖️ Disclaimer

This project and its related compiled products (Apps) are for personal technical testing, communication, and entertainment purposes only.

Do not use this tool for any illegal purposes or production environments.

The developer does not assume legal responsibility for any data loss, security issues, or system failures caused by the use of this tool.

This project follows the MIT open-source license.
