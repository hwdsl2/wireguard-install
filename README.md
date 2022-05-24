[English](README.md) | [中文](README-zh.md)

## wireguard-install

WireGuard VPN server installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS and Fedora.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used [WireGuard](https://www.wireguard.com) before.

### Installation

Run the script on your Linux server\* and follow the prompts:

```bash
wget https://get.vpnsetup.net/wg -O wireguard.sh
sudo bash wireguard.sh
```

After setup, you can run the script again to manage users or uninstall WireGuard.

[WireGuard clients](https://www.wireguard.com/install/) are available for Windows, macOS, iOS and Android.

\* A cloud server, virtual private server (VPS) or dedicated server.

### Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/wireguard-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

### License

MIT
