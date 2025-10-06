# 介绍

改进自原版 233boy/sing-box 的一键安装与管理脚本，保留原有的交互体验（`sb` 菜单、`sing-box` 命令集），同时移除推广内容并强化下载校验与运行权限设置。本项目的重构与维护得到了 OpenAI Codex 的协助，特此致谢。

# 安装

```bash
curl -fsSL https://raw.githubusercontent.com/am5188/sing-box/main/install.sh \
| sudo bash
```

- 脚本会自动计算 SHA256 并提示确认；即便通过管道执行，也会在终端要求你按 `y` 才继续。
- 如果想先下载再执行，可 `curl -O install.sh && sudo bash install.sh`，逻辑相同。
- 如需指定 sing-box 版本，可追加 `-v vX.Y.Z`；也可以使用 `-f` 指定本地 tar 包。

# 使用

- `sudo sb`：进入主菜单（添加/更改/查看/删除配置、查看状态、更新等）。
- `sudo sing-box <subcommand>`：沿用原版命令行参数（`add`、`change`、`dns` 等）。
- `sudo sing-box update`：与原版一致，可更新 core / sh / caddy；下载过程使用 TLS 校验。
- 配置文件位于 `/etc/sing-box/conf/`，日志位于 `/var/log/sing-box/`。

# 卸载

```bash
sudo sing-box uninstall
```

或手动清理：

```bash
sudo systemctl disable --now sing-box
sudo rm -rf /etc/sing-box /usr/local/bin/sing-box /var/log/sing-box
sudo sed -i '/alias sb=/d;/alias sing-box=/d' /root/.bashrc
```

# 反馈与致谢

- 项目仓库：[https://github.com/am5188/sing-box](https://github.com/am5188/sing-box)
- 原版项目：[https://github.com/233boy/sing-box](https://github.com/233boy/sing-box)

> **致谢与说明**：本仓库基于 233boy/sing-box 二次整理。原脚本一键安装、菜单化管理、协议覆盖广等特性十分优秀，为社区用户提供了极高的易用性；我们仅在此基础上移除了推广内容、改用更严格的下载校验，并增加了安全提示，操作交互保持原样。若你想保留自己的分支，直接 fork 之后把命令中的 `am5188` 改成你的 GitHub 用户名即可。

# 免责声明

本项目仅供学习与研究使用，请勿用于任何违规用途。用户须自行承担使用风险。
