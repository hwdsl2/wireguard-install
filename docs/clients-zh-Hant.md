[English](clients.md) | [简体中文](clients-zh.md) | [繁體中文](clients-zh-Hant.md) | [Русский](clients-ru.md)

# 設定 WireGuard VPN 客戶端

[WireGuard VPN 客戶端](https://www.wireguard.com/install/) 可在 Windows、macOS、iOS 和 Android 上使用。

要新增 VPN 連線，請在你的行動裝置上開啟 WireGuard 應用程式，點擊「新增」按鈕，然後掃描腳本輸出中生成的 QR 碼。對於 Windows 和 macOS，請先將生成的 `.conf` 檔案安全地傳送到你的電腦，然後開啟 WireGuard 並匯入該檔案。

要管理 WireGuard VPN 客戶端，請再次執行安裝腳本：`sudo bash wireguard.sh`。

閱讀 [:book: VPN book](vpn-book-zh-Hant.md) 以了解設定與管理 WireGuard VPN 客戶端的逐步說明。

<details>
<summary>
查看 WireGuard 腳本的使用資訊。
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
