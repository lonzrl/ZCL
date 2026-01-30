# ZCL
ZCL(ZRL Python Minecraft Launcher)
** 
 
 
一款轻量、高效、高度可定制的 Minecraft 启动器，基于 Python 开发，专为追求简洁体验与灵活配置的玩家设计。无论是原版游戏、模组整合包还是快照版本，ZCL 都能提供流畅的启动与管理体验。
✨ 核心特性
🎮 全场景版本管理
支持从 Beta 1.7.3 到最新 1.21 + 的所有官方版本
自动识别 Forge、Fabric、Quilt 等主流 Mod 加载器
版本隔离机制：每个版本独立配置目录，避免冲突
一键安装 / 卸载游戏版本，支持断点续传
🎨 灵活定制能力
可视化 JVM 参数配置（内存分配、垃圾回收器选择等）
多配置文件管理：为不同游戏场景创建独立启动配置
支持资源包、光影、材质包一键加载
自定义游戏分辨率、全屏模式等显示设置
🔐 安全稳定运行
完整的预启动检查：自动验证游戏文件完整性
优雅的错误处理机制，提供详细报错日志
支持微软账号 / 离线模式双登录
敏感信息加密存储，保护账户安全
🚀 跨平台与性能优化
原生支持 Windows（7+）、macOS（10.15+）、Linux
适配 x86-64/ARM64 架构，Apple Silicon 完美兼容
轻量化设计，低配置设备流畅运行
多线程资源下载，提升更新速度
🛠️ 快速开始
前置环境
安装 Python 3.8+：官网下载
安装 Java 运行环境（推荐 JDK 17）：
Windows：Liberica JDK
macOS/Linux：通过包管理器安装 openjdk-17-jdk
验证环境：
python --version  # 应显示3.8+
java --version    # 应显示17.0+

安装步骤
方式 1：源码安装

安装jdk_21.0.9.exe   （启动MC需要的java，在Release）
# 克隆仓库

cd ZCL

# 安装依赖
pip install -r requirements.txt

# 启动启动器
python ZCL.py

方式 2：预构建版本
前往 Releases 页面 下载对应系统的可执行文件：
Windows：dist/ZCL.exe（无需 Python 环境）
同时安装jdk_21.0.9.exe
📖 使用指南
首次启动配置

下载游戏（自动创建文件夹）
启动游戏（需要安装java）
支持litteskin账号
基本操作
功能
操作路径
安装游戏版本
版本管理 → 选择版本 → 点击 "安装"
启动游戏
主界面选择配置 → 点击 "启动游戏"
添加 Mod
配置编辑 → Mod 管理 → 拖拽 Mod 文件至列表
导入资源包
配置编辑 → 资源包 → 选择本地资源包文件

推荐 JVM 参数配置
根据内存大小选择优化参数（在 "配置编辑→JVM 参数" 中设置）：
# 4GB内存（原版/轻量模组）
-Xmx3G -Xms1G -XX:+UseG1GC -XX:MaxGCPauseMillis=200

# 8GB内存（光影/大型整合包）
-Xmx6G -Xms2G -XX:+UnlockExperimentalVMOptions -XX:+UseZGC

⚙️ 高级功能
配置文件自定义
ZCL 的配置文件为 JSON 格式，位于：
Windows：%APPDATA%\ZCL\config.json
macOS/Linux：~/.zcl/config.json
示例高级配置：
{
  "defaultProfile": "Modded-1.20",
  "autoConnectServer": {
    "address": "mc.hypixel.net",
    "port": 25565
  },
  "gameSettings": {
    "resolution": "1920x1080",
    "fullscreen": true,
    "showFPS": true
  },
  "download": {
    "threadCount": 8,
    "cacheExpireHours": 24
  }
}

批量管理工具
通过命令行接口（CLI）批量操作：
# 批量安装多个版本
python cli.py install 1.19.4 1.20.1 1.21.1

# 导出当前配置
python cli.py export-profile "MyProfile" --path ./backup

# 清理缓存文件
python cli.py clean-cache

🐛 常见问题排查
启动失败
检查 Java 版本是否与游戏版本匹配（1.18 + 需 Java 17+）
验证游戏文件完整性：版本管理 → 右键版本 → 验证文件
查看日志文件：ZCL/logs/latest.log
关闭冲突软件（如杀毒软件、内存清理工具）
游戏卡顿
降低渲染距离和仿真距离
关闭高开销特效（光影、粒子效果）
调整 JVM 内存分配（避免设置过高导致系统卡顿）
安装优化类 Mod（如 Sodium、Lithium）
模组冲突
使用 "模组冲突检测" 功能（配置编辑→Mod 管理→检测冲突）
按安装时间倒序禁用模组，定位冲突源
确保所有 Mod 与游戏版本、加载器版本匹配
🤝 贡献指南
欢迎通过以下方式参与项目开发：
提交 Bug 报告：在 Issues 中提供详细的复现步骤和日志
功能建议：在 Discussions 中分享你的想法
代码贡献：
Fork 本仓库
创建特性分支（feature/xxx）
提交代码并创建 Pull Request
确保代码通过 flake8 格式检查
开发环境搭建：
# 安装开发依赖
pip install -r requirements-dev.txt

# 运行测试
pytest tests/

📄 许可证
本项目采用 GNU V3.0 许可证开源 - 详见 LICENSE 文件
📞 联系我们
项目地址：GitHub
问题反馈：Issues
讨论社区：Discussions
