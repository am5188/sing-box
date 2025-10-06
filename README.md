# 介绍

改进自原版 233boy/sing-box 的一键安装与管理脚本，保留原有的交互体验（`sb` 菜单、`sing-box` 命令集），同时移除推广内容并强化下载校验与运行权限设置。

# 安装

```bash
curl -fsSL https://raw.githubusercontent.com/am5188/sing-box/main/install.sh \
| sudo bash
```

- 脚本会自动计算下载包的 SHA256 并提示，只有你确认后才继续安装。
- 如需指定 sing-box 版本，可追加 `-v vX.Y.Z`；也可以使用 `-f` 指定本地 tar 包。
- 安装完成后会生成 `sb`（菜单）与 `sing-box` 命令，逻辑与原版一致。

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

# 反馈

- 项目仓库：[https://github.com/am5188/sing-box](https://github.com/am5188/sing-box)
- 原版项目：[https://github.com/233boy/sing-box](https://github.com/233boy/sing-box)

# 免责声明

本项目仅供学习与研究使用，请勿用于任何违规用途。用户须自行承担使用风险。
