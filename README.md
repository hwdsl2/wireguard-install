[English](README.md) | [中文](README-zh.md) | [Video en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# WireGuard VPN Server Auto Setup Script

[![Build Status](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml/badge.svg)](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml) &nbsp;[![License: MIT](docs/images/license.svg)](https://opensource.org/licenses/MIT)

WireGuard VPN server installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS, Fedora, openSUSE and Raspberry Pi OS.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used WireGuard before. [WireGuard](https://www.wireguard.com) is a fast and modern VPN designed with the goals of ease of use and high performance.

See also: [OpenVPN](https://github.com/hwdsl2/openvpn-install) and [IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) server auto setup scripts.

**[&raquo; :book: Book: Build Your Own VPN Server](docs/vpn-book.md)** [[English](https://books2read.com/vpnguide?store=amazon) | [中文](https://books2read.com/vpnguidezh) | [Español](https://books2read.com/vpnguidees?store=amazon) | [Deutsch](https://books2read.com/vpnguidede?store=amazon) | [Français](https://books2read.com/vpnguidefr?store=amazon) | [Italiano](https://books2read.com/vpnguideit?store=amazon) | [日本語](https://books2read.com/vpnguideja?store=amazon)]

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

\* A cloud server, virtual private server (VPS) or dedicated server.

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

For servers with an external firewall (e.g. [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/firewall/docs/firewalls)), open UDP port 51820 for the VPN.

**Option 2:** Interactive install using custom options.

```bash
sudo bash wireguard.sh
```

You can customize the following options: VPN server's DNS name, UDP port, DNS server for VPN clients and name of the first client.

For servers with an external firewall, open your selected UDP port for the VPN.

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

Advanced users can auto install WireGuard using custom options, by specifying command-line options when running the script. For more details, see the next section "view usage information for the WireGuard script".

Alternatively, you may provide a Bash "here document" as input to the setup script. This method can also be used to provide input to manage users after install.

First, install WireGuard interactively using custom options, and write down all your inputs to the script.

```bash
sudo bash wireguard.sh
```

If you need to remove WireGuard, run the script again and select the appropriate option.

Next, create the custom install command using your inputs. Example:

```bash
sudo bash wireguard.sh <<ANSWERS
n
51820
client
2
y
ANSWERS
```

**Note:** The install options may change in future versions of the script.
</details>
<details>
<summary>
View usage information for the WireGuard script.
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

## Next steps

After setup, you can run the script again to manage users or uninstall WireGuard.

Get your computer or device to use the VPN. Please refer to:

**[Configure WireGuard VPN Clients](docs/clients.md)**

**Read [:book: VPN book](docs/vpn-book.md) to access [extra content](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J).**

Enjoy your very own VPN! :sparkles::tada::rocket::sparkles:

## Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/wireguard-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

<details>
<summary>
List of enhancements over Nyr/wireguard-install.
</summary>

- Improved compatibility with Setup IPsec VPN
- Improved script reliability, user input and output
- Supports auto install using default or custom options
- Supports using a DNS name as server address
- Added support for openSUSE Linux
- Supports listing existing VPN clients
- Supports showing QR code for a client
- Supports custom DNS server(s) for VPN clients
- Supports command-line options for managing VPN clients
- Optimizes `sysctl` settings for improved VPN performance
- Improved creation of client config files when using `sudo`

...and more!
</details>

## License

MIT
