[English](README.md) | [中文](README-zh.md)

## wireguard-install

使用 Linux 脚本一键快速搭建自己的 WireGuard VPN 服务器。支持 Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS 和 Fedora 系统。

该脚本可让你在几分钟内建立自己的 VPN 服务器，即使你以前没有使用过 [WireGuard](https://www.wireguard.com)。

### 安装说明

在你的 Linux 服务器\* 上运行脚本，并按提示操作：

```bash
wget https://get.vpnsetup.net/wg -O wireguard.sh
sudo bash wireguard.sh
```

安装完成后，你可以再次运行脚本来管理用户或卸载 WireGuard。

[WireGuard 客户端](https://www.wireguard.com/install/) 在 Windows, macOS, iOS 和 Android 上可用。

\* 一个云服务器，虚拟专用服务器 (VPS) 或者专用服务器。

### 致谢

此脚本基于 [Nyr 和 contributors](https://github.com/Nyr/wireguard-install) 的出色工作，并进行了增强和更改以与 [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) 项目兼容。

### 授权协议

MIT
