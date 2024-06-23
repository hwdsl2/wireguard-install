[English](clients.md) | [中文](clients-zh.md)

# Configure WireGuard VPN Clients

[WireGuard VPN clients](https://www.wireguard.com/install/) are available for Windows, macOS, iOS and Android.

To add a VPN connection, open the WireGuard App on your mobile device, tap the "Add" button, then scan the generated QR code in the script output. For Windows and macOS, first securely transfer the generated `.conf` file to your computer, then open WireGuard and import the file.

To manage WireGuard VPN clients, run the install script again: `sudo bash wireguard.sh`.

Read [:book: VPN book](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J) to learn step-by-step instructions to configure and manage WireGuard VPN clients.

<details>
<summary>
View usage information for the WireGuard script.
</summary>

```
Usage: bash wireguard.sh [options]

Options:
  --auto                        auto install WireGuard using default options
  --addclient [client name]     add a new client
  --dns1 [DNS server IP]        primary DNS server for new client (optional, defaults to Google Public DNS)
  --dns2 [DNS server IP]        secondary DNS server for new client (optional)
  --listclients                 list the names of existing clients
  --removeclient [client name]  remove an existing client
  --showclientqr [client name]  show QR code for an existing client
  --uninstall                   remove WireGuard and delete all configuration
  -y, --yes                     assume "yes" as answer to prompts when removing a client or removing WireGuard
  -h, --help                    show this help message and exit

To customize install options, run this script without arguments.
```
</details>
