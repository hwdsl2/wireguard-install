[English](README.md) | [中文](README-zh.md)

# WireGuard VPN Server Auto Setup Script

WireGuard VPN server installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS and Fedora.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used WireGuard before. [WireGuard](https://www.wireguard.com) is a fast and modern VPN designed with the goals of ease of use and high performance.

[**&raquo; See also: OpenVPN Server Auto Setup Script**](https://github.com/hwdsl2/openvpn-install)

## Installation

Run the script on your Linux server\* and follow the prompts:

```bash
wget https://get.vpnsetup.net/wg -O wireguard.sh
sudo bash wireguard.sh
```

<details>
<summary>
Alternative commands.
</summary>

You may also use `curl` to download:

```bash
curl -fL https://get.vpnsetup.net/wg -o wireguard.sh
sudo bash wireguard.sh
```

Alternative setup URL:

```bash
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
```

If you are unable to download, open [wireguard-install.sh](wireguard-install.sh), then click the `Raw` button on the right. Press `Ctrl/Cmd+A` to select all, `Ctrl/Cmd+C` to copy, then paste into your favorite editor.
</details>

\* A cloud server, virtual private server (VPS) or dedicated server.

## Next steps

After setup, you can run the script again to manage users or uninstall WireGuard.

[WireGuard VPN clients](https://www.wireguard.com/install/) are available for Windows, macOS, iOS and Android. To add a VPN connection, open the WireGuard App on your device, click on the "Add" button, then scan the generated QR code in the script output.

Enjoy your very own VPN! :sparkles::tada::rocket::sparkles:

## Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/wireguard-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

## License

MIT
