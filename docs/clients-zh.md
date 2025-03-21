[English](clients.md) | [中文](clients-zh.md)

# 配置 WireGuard VPN 客户端

[WireGuard VPN 客户端](https://www.wireguard.com/install/) 在 Windows, macOS, iOS 和 Android 上可用。

要添加 VPN 连接，请在你的移动设备上打开 WireGuard 应用程序，单击 "添加" 按钮，然后扫描脚本输出中生成的二维码。对于 Windows 和 macOS，首先将生成的 `.conf` 文件安全地传送到你的计算机，然后打开 WireGuard 并导入文件。

要管理 WireGuard VPN 客户端，请再次运行安装脚本：`sudo bash wireguard.sh`。

阅读 [:book: VPN book](vpn-book-zh.md) 以了解配置和管理 WireGuard VPN 客户端的分步说明。

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
