## wireguard-install

WireGuard [road warrior](http://en.wikipedia.org/wiki/Road_warrior_%28computing%29) installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS and Fedora.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used [WireGuard](https://www.wireguard.com) before. It has been designed to be as unobtrusive and universal as possible.

### Installation

Run the script on your Linux server\* and follow the prompts:

```bash
wget https://get.vpnsetup.net/wg -nv -O wireguard.sh
sudo bash wireguard.sh
```

You can run the script again after install to manage users or uninstall WireGuard.

\* A cloud server, virtual private server (VPS) or dedicated server.

### Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/wireguard-install), with changes to improve compatibility with the Setup IPsec VPN project. Please report any issues to the linked upstream repository.

### License

MIT
