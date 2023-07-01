[English](README.md) | [中文](README-zh.md) | [Vídeo en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# WireGuard VPN Server Auto Setup Script

[![Build Status](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml/badge.svg)](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml) &nbsp;[![License: MIT](docs/images/license.svg)](https://opensource.org/licenses/MIT)

WireGuard VPN server installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS and Fedora.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used WireGuard before. [WireGuard](https://www.wireguard.com) is a fast and modern VPN designed with the goals of ease of use and high performance.

See also: [OpenVPN](https://github.com/hwdsl2/openvpn-install) and [IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) server auto setup scripts.

**[&raquo; :book: Book: Build Your Own VPN Server: A Step by Step Guide](https://books2read.com/vpnguide)**

## Features

- Fully automated WireGuard VPN server setup, no user input needed
- Supports interactive install using custom options
- Generates VPN profiles to auto-configure Windows, macOS, iOS and Android devices
- Supports managing WireGuard VPN users
- Optimizes `sysctl` settings for improved VPN performance

## Installation

First, download the script on your Linux server\*:

```bash
wget -O wireguard.sh https://get.vpnsetup.net/wg
```

**Option 1:** Auto install WireGuard using default options.

```bash
sudo bash wireguard.sh --auto
```

<details>
<summary>
See the script in action (terminal recording).
</summary>

**Note:** This recording is for demo purposes only.

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>

For servers with an external firewall (e.g. [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/vpc/docs/firewalls)), open UDP port 51820 for the VPN.

**Option 2:** Interactive install using custom options.

```bash
sudo bash wireguard.sh
```

<details>
<summary>
Click here if you are unable to download.
</summary>

You may also use `curl` to download:

```bash
curl -fL -o wireguard.sh https://get.vpnsetup.net/wg
```

Then follow the instructions above to install.

Alternative setup URLs:

```bash
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
https://gitlab.com/hwdsl2/wireguard-install/-/raw/master/wireguard-install.sh
```

If you are unable to download, open [wireguard-install.sh](wireguard-install.sh), then click the `Raw` button on the right. Press `Ctrl/Cmd+A` to select all, `Ctrl/Cmd+C` to copy, then paste into your favorite editor.
</details>
<details>
<summary>
Advanced: Auto install using custom options.
</summary>

Advanced users can auto install WireGuard using custom options, by providing a Bash "here document" as input to the setup script. This method can also be used to provide input to manage users after install.

First, install WireGuard interactively using custom options, and write down all your inputs to the script.

```bash
sudo bash wireguard.sh
```

If you need to remove WireGuard, run the script again and select the appropriate option.

Next, create the custom install command using your inputs. Example:

```bash
sudo bash wireguard.sh <<ANSWERS
51820
client
2
y
ANSWERS
```

**Note:** The install options may change in future versions of the script.
</details>

\* A cloud server, virtual private server (VPS) or dedicated server.

## Next steps

After setup, you can run the script again to manage users or uninstall WireGuard.

Get your computer or device to use the VPN. Please refer to:

**[Configure WireGuard VPN Clients](docs/clients.md)**

**Read [:book: VPN book](https://books2read.com/vpn) to access [extra content](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J).**

Enjoy your very own VPN! :sparkles::tada::rocket::sparkles:

## Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/wireguard-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

<details>
<summary>
List of enhancements over Nyr/wireguard-install.
</summary>

- Improved compatibility with Setup IPsec VPN
- Improved script reliability, user input and output
- Supports auto install using default options
- Supports listing existing VPN clients
- Supports custom DNS server(s) for VPN clients
- Optimizes `sysctl` settings for improved VPN performance
- Improved creation of client config files when using `sudo`

...and more!
</details>

## License

MIT
