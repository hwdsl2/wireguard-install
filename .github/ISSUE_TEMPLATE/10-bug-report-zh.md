---
name: 错误报告
about: 请使用这个模板来提交 bug
title: ''
labels: ''
assignees: ''

---

**任务列表**

- [ ] 我已阅读[自述文件](https://github.com/hwdsl2/wireguard-install/blob/master/README-zh.md)
- [ ] 我已按照说明[配置 VPN 客户端](https://github.com/hwdsl2/wireguard-install/blob/master/docs/clients-zh.md)
- [ ] 我搜索了已有的 [Issues](https://github.com/hwdsl2/wireguard-install/issues?q=is%3Aissue)
- [ ] 这个 bug 是关于 VPN 安装脚本，而不是 WireGuard VPN 本身

<!---
发布日志或配置前，请删除私钥、VPN 客户端配置文件、不想公开的服务器地址和其它敏感信息。
--->

**问题描述**
使用清楚简明的语言描述这个 bug。

**重现步骤**
重现该 bug 的步骤：

1. ...
2. ...

**期待的正确结果**
简要地描述你期望的正确结果。

**日志**
添加相关错误日志以帮助解释该问题（如果适用）。

常用命令包括：

```bash
sudo systemctl status wg-quick@wg0
sudo journalctl -u wg-quick@wg0 -n 50
sudo wg show
```

如果问题可能与防火墙规则有关，也请提供：

```bash
sudo systemctl status wg-iptables
sudo journalctl -u wg-iptables -n 50
```

**服务器信息（请填写以下信息）**
- 操作系统和版本: [比如 Debian 13]
- 架构: [比如 x86_64, arm64]
- 服务提供商（如果适用）: [比如 GCP, AWS]
- 外部防火墙/NAT: [比如 UDP 51820 已开放，自定义 UDP 端口已开放，不适用]
- 使用的脚本命令: [比如 `sudo bash wireguard.sh --auto`, `sudo bash wireguard.sh --addclient client2`]
- 自定义安装选项（如果使用）: [比如 `--serveraddr`, `--port`, `--clientname`, `--dns1`, `--dns2`]

**客户端信息（如果适用，请填写以下信息）**
- 设备: [比如 iPhone 15]
- 操作系统和版本: [比如 iOS 18]
- WireGuard 应用版本: [比如 WireGuard 1.x]
- 配置方式: [扫描二维码，导入 `.conf` 文件，手动配置]

**配置**
如果相关，请提供 `/etc/wireguard/wg0.conf` 中的片段，并删除敏感信息。不要包含私钥或完整的客户端配置文件。

**其它信息**
添加关于该 bug 的其它信息。
