[English](README.md) | [中文](README-zh.md) | [Video en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# WireGuard VPN 服务器一键安装脚本

[![Build Status](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml/badge.svg)](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml) &nbsp;[![License: MIT](docs/images/license.svg)](https://opensource.org/licenses/MIT)

使用 Linux 脚本一键快速搭建自己的 WireGuard VPN 服务器。支持 Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS, Fedora, openSUSE 和 Raspberry Pi OS。

该脚本可让你在几分钟内建立自己的 VPN 服务器，即使你以前没有使用过 WireGuard。[WireGuard](https://www.wireguard.com) 是一种快速且现代的 VPN，其设计目标是易于使用和高性能。

另见：[OpenVPN](https://github.com/hwdsl2/openvpn-install/blob/master/README-zh.md) 和 [IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn/blob/master/README-zh.md) 服务器一键安装脚本。

**[&raquo; :book: Book: 搭建自己的 VPN 服务器分步指南](docs/vpn-book-zh.md)** [[中文](https://books2read.com/vpnguidezh) | [English](https://books2read.com/vpnguide?store=amazon) | [Español](https://books2read.com/vpnguidees?store=amazon) | [Deutsch](https://books2read.com/vpnguidede?store=amazon) | [Français](https://books2read.com/vpnguidefr?store=amazon) | [Italiano](https://books2read.com/vpnguideit?store=amazon) | [日本語](https://books2read.com/vpnguideja?store=amazon)]

## 功能特性

- 全自动的 WireGuard VPN 服务器配置，无需用户输入
- 支持使用自定义选项进行交互式安装
- 生成 VPN 配置文件以自动配置 Windows, macOS, iOS 和 Android 设备
- 支持管理 WireGuard VPN 用户
- 优化 `sysctl` 设置以提高 VPN 性能

## 安装说明

首先在你的 Linux 服务器\* 上下载脚本：

```bash
wget -O wireguard.sh https://get.vpnsetup.net/wg
```

\* 一个云服务器，虚拟专用服务器 (VPS) 或者专用服务器。

**选项 1:** 使用默认选项自动安装 WireGuard。

```bash
sudo bash wireguard.sh --auto
```

<details>
<summary>
查看脚本的示例输出（终端记录）。
</summary>

**注：** 此终端记录仅用于演示目的。

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>

对于有外部防火墙的服务器（比如 [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/firewall/docs/firewalls)），请为 VPN 打开 UDP 端口 51820。

**选项 2:** 使用自定义选项进行交互式安装。

```bash
sudo bash wireguard.sh
```

你可以自定义以下选项：VPN 服务器的域名，UDP 端口，VPN 客户端的 DNS 服务器以及第一个客户端的名称。

对于有外部防火墙的服务器，请为 VPN 打开所选的 UDP 端口。

<details>
<summary>
如果无法下载，请点这里。
</summary>

你也可以使用 `curl` 下载：

```bash
curl -fL -o wireguard.sh https://get.vpnsetup.net/wg
```

然后按照上面的说明安装。

或者，你也可以使用这些链接：

```bash
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
https://gitlab.com/hwdsl2/wireguard-install/-/raw/master/wireguard-install.sh
```

如果无法下载，打开 [wireguard-install.sh](wireguard-install.sh)，然后点击右边的 `Raw` 按钮。按快捷键 `Ctrl/Cmd+A` 全选，`Ctrl/Cmd+C` 复制，然后粘贴到你喜欢的编辑器。
</details>
<details>
<summary>
高级：使用自定义选项自动安装。
</summary>

高级用户可以使用自定义选项自动安装 WireGuard，方法是在运行脚本时指定命令行参数。有关更多信息，请参见下一节，查看 WireGuard 脚本的使用信息。

或者，你也可以提供一个 Bash "here document" 作为安装脚本的输入。此方法还可用于在安装后提供输入以管理用户。

首先，使用自定义选项以交互方式安装 WireGuard，并写下你对脚本的所有输入值。

```bash
sudo bash wireguard.sh
```

如需删除 WireGuard，请再次运行脚本并选择适当的选项。

然后使用你的输入值创建自定义安装命令。例如：

```bash
sudo bash wireguard.sh <<ANSWERS
n
51820
client
2
y
ANSWERS
```

**注：** 安装选项可能会在脚本的未来版本中发生变化。
</details>
<details>
<summary>
查看 WireGuard 脚本的使用信息。
</summary>

```
Usage: bash wireguard.sh [options]

Options:

  --addclient [client name]      add a new client
  --dns1 [DNS server IP]         primary DNS server for new client (optional, default: Google Public DNS)
  --dns2 [DNS server IP]         secondary DNS server for new client (optional)
  --listclients                  list the names of existing clients
  --removeclient [client name]   remove an existing client
  --showclientqr [client name]   show QR code for an existing client
  --uninstall                    remove WireGuard and delete all configuration
  -y, --yes                      assume "yes" as answer to prompts when removing a client or removing WireGuard
  -h, --help                     show this help message and exit

Install options (optional):

  --auto                         auto install WireGuard using default or custom options
  --serveraddr [DNS name or IP]  server address, must be a fully qualified domain name (FQDN) or an IPv4 address
  --port [number]                port for WireGuard (1-65535, default: 51820)
  --clientname [client name]     name for the first WireGuard client (default: client)
  --dns1 [DNS server IP]         primary DNS server for first client (default: Google Public DNS)
  --dns2 [DNS server IP]         secondary DNS server for first client

To customize options, you may also run this script without arguments.
```
</details>

## 下一步

安装完成后，你可以再次运行脚本来管理用户或者卸载 WireGuard。

配置你的计算机或其它设备使用 VPN。请参见：

**[配置 WireGuard VPN 客户端](docs/clients-zh.md)**

**阅读 [:book: VPN book](docs/vpn-book-zh.md) 以访问 [额外内容](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-X8X5FVFZC)。**

开始使用自己的专属 VPN! :sparkles::tada::rocket::sparkles:

## 致谢

此脚本基于 [Nyr 和 contributors](https://github.com/Nyr/wireguard-install) 的出色工作，并进行了增强和更改以与 [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) 项目兼容。

<details>
<summary>
对 Nyr/wireguard-install 的改进列表。
</summary>

- 改进了与 Setup IPsec VPN 的兼容性
- 改进了脚本的可靠性，用户输入和输出
- 支持使用默认或自定义选项自动安装
- 支持使用域名作为服务器地址
- 增加了对 openSUSE Linux 的支持
- 支持列出现有的 VPN 客户端
- 支持显示客户端配置的二维码
- 支持为 VPN 客户端自定义 DNS 服务器
- 支持使用命令行参数管理 VPN 客户端
- 优化 `sysctl` 设置以提高 VPN 性能
- 使用 `sudo` 时改进了客户端配置文件的创建

...和更多！
</details>

## 授权协议

MIT
