[English](README.md) | [简体中文](README-zh.md) | [繁體中文](README-zh-Hant.md) | [Русский](README-ru.md) | [日本語](README-ja.md) | [Video en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# WireGuard VPN サーバー自動セットアップスクリプト

[![Build Status](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml/badge.svg)](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml) [![GitHub Stars](https://raw.githubusercontent.com/hwdsl2/badges/main/img/github-stars-wireguard-install.svg)](https://github.com/hwdsl2/wireguard-install/stargazers) [![License: MIT](docs/images/license.svg)](https://opensource.org/licenses/MIT)

Ubuntu、Debian、AlmaLinux、Rocky Linux、CentOS、Fedora、openSUSE、Raspberry Pi OS 向けの WireGuard VPN サーバーインストーラーです。

このスクリプトを使えば、WireGuard を使ったことがなくても、ほんの数分で自分専用の VPN サーバーをセットアップできます。[WireGuard](https://www.wireguard.com) は、使いやすさと高いパフォーマンスを目標に設計された、高速でモダンな VPN です。

**特長:**

- WireGuard VPN サーバーのセットアップを完全に自動化、ユーザー入力は不要
- カスタムオプションを使った対話形式のインストールにも対応
- Windows、macOS、iOS、Android の各デバイスを自動設定する VPN プロファイルを生成
- モバイルデバイスを簡単にセットアップできる QR コードを生成
- WireGuard VPN ユーザーの管理に対応
- VPN パフォーマンス向上のため `sysctl` 設定を最適化
- VPN クライアント向けに IPv4 と IPv6 のデュアルスタックをサポート

**その他のプロジェクト:**

- **Docker VPN:** [WireGuard](https://github.com/hwdsl2/docker-wireguard), [OpenVPN](https://github.com/hwdsl2/docker-openvpn), [IPsec VPN](https://github.com/hwdsl2/docker-ipsec-vpn-server), [Headscale](https://github.com/hwdsl2/docker-headscale)
- **AI:** ローカル LLM、チャット、RAG、音声、AI ツール向けの [Self-Hosted AI Stack](https://github.com/hwdsl2/self-hosted-ai-stack)
- **書籍:** [Build Your Own VPN Server](https://books2read.com/vpnguide) · [The Self-Hosted AI Builder’s Guide](https://books2read.com/aiguide)

## インストール

まず、Linux サーバー\*でスクリプトをダウンロードします:

```bash
wget -O wireguard.sh https://get.vpnsetup.net/wg
```

\* クラウドサーバー、仮想専用サーバー (VPS)、または専用サーバー。

**オプション 1:** デフォルトオプションで WireGuard を自動インストールします。

```bash
sudo bash wireguard.sh --auto
```

<details>
<summary>
スクリプトの実際の動作を見る (ターミナルの録画)。
</summary>

**注意:** この録画はデモ目的のみのものです。

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>

**ヒント:** 必要に応じて、同じサーバーに [OpenVPN](https://github.com/hwdsl2/openvpn-install)、[IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn)、[Headscale](https://github.com/hwdsl2/headscale-install) をインストールすることもできます。

外部ファイアウォールのあるサーバー (例: [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/firewall/docs/firewalls)) では、VPN 用に UDP ポート 51820 を開放してください。

**オプション 2:** カスタムオプションを使った対話形式のインストール。

```bash
sudo bash wireguard.sh
```

次のオプションをカスタマイズできます: VPN サーバーの DNS 名、UDP ポート、VPN クライアント用の DNS サーバー、最初のクライアントの名前。

外部ファイアウォールのあるサーバーでは、選択した UDP ポートを VPN 用に開放してください。

<details>
<summary>
ダウンロードできない場合はこちらをクリック。
</summary>

`curl` を使ってダウンロードすることもできます:

```bash
curl -fL -o wireguard.sh https://get.vpnsetup.net/wg
```

その後、上記の手順に従ってインストールします。

代替のセットアップ URL:

```bash
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
https://gitlab.com/hwdsl2/wireguard-install/-/raw/master/wireguard-install.sh
```

ダウンロードできない場合は、[wireguard-install.sh](wireguard-install.sh) を開き、右側の `Raw` ボタンをクリックします。`Ctrl/Cmd+A` ですべて選択し、`Ctrl/Cmd+C` でコピーして、お好みのエディターに貼り付けてください。
</details>
<details>
<summary>
上級者向け: カスタムオプションを使った自動インストール。
</summary>

上級者は、スクリプトの実行時にコマンドラインオプションを指定することで、カスタムオプションを使って WireGuard を自動インストールできます。詳しくは、次のセクション「WireGuard スクリプトの使い方を表示する」を参照してください。

あるいは、セットアップスクリプトへの入力として Bash の「ヒアドキュメント」を渡すこともできます。この方法は、インストール後にユーザーを管理するための入力を渡す場合にも使えます。

まず、カスタムオプションを使って WireGuard を対話形式でインストールし、スクリプトへのすべての入力を書き留めておきます。

```bash
sudo bash wireguard.sh
```

WireGuard を削除する必要がある場合は、スクリプトを再度実行して適切なオプションを選択してください。

次に、書き留めた入力を使ってカスタムインストールコマンドを作成します。例:

```bash
sudo bash wireguard.sh <<ANSWERS
n
51820
client
2
y
ANSWERS
```

**注意:** インストールオプションは、今後のバージョンのスクリプトで変更される可能性があります。
</details>
<details>
<summary>
WireGuard スクリプトの使い方を表示する。
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

## コミュニティ

- 📬 [プロジェクトの更新情報と無料のデプロイガイドを受け取る](https://selfhostedstack.beehiiv.com/subscribe?utm_campaign=vpn) (月に 1～2 通のメール)
- 💬 ディスカッションのために [r/selfhostedstack](https://www.reddit.com/r/selfhostedstack/) コミュニティに参加する
- ⭐ 役に立ったと感じたらリポジトリにスターを付けてください — 他の人が見つけやすくなります

## 次のステップ

セットアップ後は、スクリプトを再度実行してユーザーを管理したり、WireGuard をアンインストールしたりできます。

お使いのコンピューターやデバイスで VPN を使えるようにしましょう。次を参照してください:

**[WireGuard VPN クライアントを設定する](docs/clients.md)**

**[📘 VPN book](docs/vpn-book.md) を読んで[追加コンテンツ](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J)にアクセスしましょう。**

自分だけの VPN をお楽しみください! :sparkles::tada::rocket::sparkles:

## クレジット

このスクリプトは、[Nyr and contributors](https://github.com/Nyr/wireguard-install) の素晴らしい成果を基に、[Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) プロジェクトとの互換性のための機能強化と変更を加えたものです。

<details>
<summary>
Nyr/wireguard-install に対する機能強化の一覧。
</summary>

- Setup IPsec VPN との互換性を改善
- スクリプトの信頼性、ユーザー入力と出力を改善
- デフォルトまたはカスタムオプションを使った自動インストールに対応
- サーバーアドレスとして DNS 名を使用することに対応
- openSUSE Linux のサポートを追加
- 既存の VPN クライアントの一覧表示に対応
- クライアントの QR コード表示に対応
- VPN クライアント向けのカスタム DNS サーバーに対応
- VPN クライアント管理のためのコマンドラインオプションに対応
- VPN パフォーマンス向上のため `sysctl` 設定を最適化
- `sudo` 使用時のクライアント設定ファイルの作成を改善

...その他にもたくさん!
</details>

## ライセンス

MIT
