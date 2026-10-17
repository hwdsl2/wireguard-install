# Contributing

Thanks for helping improve this project. This repository maintains the bare-metal WireGuard install script; Docker image changes belong in [docker-wireguard](https://github.com/hwdsl2/docker-wireguard).

## Before You Start

- Search existing issues and pull requests.
- Keep changes focused and easy to review.
- For upstream WireGuard behavior, check the upstream project first.
- Do not include private keys, client `.conf` files, VPN credentials, or logs with secrets.

## Pull Requests

- Update `README.md` or docs when install behavior, options, service names, paths, or defaults change.
- Include the tested Linux distribution, version, architecture, hosting environment, and WireGuard port.
- Note whether install, add/remove client, QR display, or uninstall paths were tested.

## Testing

Test the smallest relevant path before opening a PR, for example:

- Run ShellCheck when editing shell scripts.
- Test install or client-management paths touched by the change.
- Check `systemctl status wg-quick@wg0`, `journalctl`, and `wg show` for runtime changes.
- Verify client docs when changing generated configs or QR behavior.
