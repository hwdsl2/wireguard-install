---
name: Bug report
about: Tell us about a problem you are experiencing
title: ''
labels: ''
assignees: ''

---

**Checklist**

- [ ] I read the [README](https://github.com/hwdsl2/wireguard-install/blob/master/README.md)
- [ ] I followed instructions to [configure VPN clients](https://github.com/hwdsl2/wireguard-install/blob/master/docs/clients.md)
- [ ] I searched existing [Issues](https://github.com/hwdsl2/wireguard-install/issues?q=is%3Aissue)
- [ ] This bug is about the VPN setup script, and not WireGuard VPN itself

<!---
Before posting logs or configuration, remove private keys, VPN client configuration files, server addresses you do not want public, and other secrets.
--->

**Describe the issue**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:

1. ...
2. ...

**Expected behavior**
A clear and concise description of what you expected to happen.

**Logs**
Add relevant error logs to help explain the problem, if applicable.

Useful commands include:

```bash
sudo systemctl status wg-quick@wg0
sudo journalctl -u wg-quick@wg0 -n 50
sudo wg show
```

If the issue may be related to firewall rules, also include:

```bash
sudo systemctl status wg-iptables
sudo journalctl -u wg-iptables -n 50
```

**Server (please complete the following information)**
- OS and version: [e.g. Debian 13]
- Architecture: [e.g. x86_64, arm64]
- Hosting provider (if applicable): [e.g. GCP, AWS]
- External firewall/NAT: [e.g. UDP 51820 open, custom UDP port open, not applicable]
- Script command used: [e.g. `sudo bash wireguard.sh --auto`, `sudo bash wireguard.sh --addclient client2`]
- Custom install options (if used): [e.g. `--serveraddr`, `--port`, `--clientname`, `--dns1`, `--dns2`]

**Client (please complete the following information, if applicable)**
- Device: [e.g. iPhone 15]
- OS and version: [e.g. iOS 18]
- WireGuard app version: [e.g. WireGuard 1.x]
- Setup method: [QR code, imported `.conf` file, manual configuration]

**Configuration**
If relevant, include redacted snippets from `/etc/wireguard/wg0.conf`. Do not include private keys or full client configuration files.

**Additional context**
Add any other context about the problem here.
