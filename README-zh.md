[English](README.md) | [中文](README-zh.md)

# WireGuard VPN 服务器一键安装脚本

使用 Linux 脚本一键快速搭建自己的 WireGuard VPN 服务器。支持 Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS 和 Fedora 系统。

该脚本可让你在几分钟内建立自己的 VPN 服务器，即使你以前没有使用过 WireGuard。[WireGuard](https://www.wireguard.com) 是一种快速且现代的 VPN，其设计目标是易于使用和高性能。

[**&raquo; 另见：OpenVPN 服务器一键安装脚本**](https://github.com/hwdsl2/openvpn-install/blob/master/README-zh.md)

## 安装说明

在你的 Linux 服务器\* 上运行脚本，并按提示操作：

```bash
wget https://get.vpnsetup.net/wg -O wireguard.sh
sudo bash wireguard.sh
```

<details>
<summary>
或者，你也可以使用以下命令。
</summary>

你也可以使用 `curl` 下载：

```bash
curl -fL https://get.vpnsetup.net/wg -o wireguard.sh
sudo bash wireguard.sh
```

或者，你也可以使用这个链接：

```bash
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
```

如果无法下载，打开 [wireguard-install.sh](wireguard-install.sh)，然后点击右边的 `Raw` 按钮。按快捷键 `Ctrl/Cmd+A` 全选，`Ctrl/Cmd+C` 复制，然后粘贴到你喜欢的编辑器。
</details>

\* 一个云服务器，虚拟专用服务器 (VPS) 或者专用服务器。

## 下一步

安装完成后，你可以再次运行脚本来管理用户或者卸载 WireGuard。

[WireGuard VPN 客户端](https://www.wireguard.com/install/) 在 Windows, macOS, iOS 和 Android 上可用。要添加 VPN 连接，请在你的设备上打开 WireGuard 应用程序，单击 "添加" 按钮，然后扫描脚本输出中生成的二维码。

开始使用自己的专属 VPN! :sparkles::tada::rocket::sparkles:

## 致谢

此脚本基于 [Nyr 和 contributors](https://github.com/Nyr/wireguard-install) 的出色工作，并进行了增强和更改以与 [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) 项目兼容。

## 授权协议

MIT
