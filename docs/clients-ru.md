[English](clients.md) | [简体中文](clients-zh.md) | [繁體中文](clients-zh-Hant.md) | [Русский](clients-ru.md)

# Настройка клиентов WireGuard VPN

[Клиенты WireGuard VPN](https://www.wireguard.com/install/) доступны для Windows, macOS, iOS и Android.

Чтобы добавить VPN-подключение, откройте приложение WireGuard на мобильном устройстве, нажмите кнопку «Add», затем отсканируйте сгенерированный QR-код, показанный в выводе скрипта. Для Windows и macOS сначала безопасно перенесите сгенерированный файл `.conf` на ваш компьютер, затем откройте WireGuard и импортируйте этот файл.

Чтобы управлять клиентами WireGuard VPN, снова запустите установочный скрипт: `sudo bash wireguard.sh`.

Прочитайте [:book: книгу о VPN](vpn-book.md), чтобы получить пошаговые инструкции по настройке и управлению клиентами WireGuard VPN.

<details>
<summary>
Просмотреть информацию об использовании скрипта WireGuard.
</summary>

```
Usage: bash wireguard.sh [options]

Options:

  --addclient [client name]      добавить нового клиента
  --dns1 [DNS server IP]         основной DNS-сервер для нового клиента (необязательно, по умолчанию: Google Public DNS)
  --dns2 [DNS server IP]         резервный DNS-сервер для нового клиента (необязательно)
  --listclients                  показать список существующих клиентов
  --removeclient [client name]   удалить существующего клиента
  --showclientqr [client name]   показать QR-код для существующего клиента
  --uninstall                    удалить WireGuard и удалить всю конфигурацию
  -y, --yes                      автоматически отвечать "yes" на запросы при удалении клиента или WireGuard
  -h, --help                     показать это сообщение справки и выйти

Параметры установки (необязательно):

  --auto                         автоматически установить WireGuard с параметрами по умолчанию или пользовательскими параметрами
  --serveraddr [DNS name or IP]  адрес сервера, должен быть полным доменным именем (FQDN) или IPv4-адресом
  --port [number]                порт для WireGuard (1–65535, по умолчанию: 51820)
  --clientname [client name]     имя первого клиента WireGuard (по умолчанию: client)
  --dns1 [DNS server IP]         основной DNS-сервер для первого клиента (по умолчанию: Google Public DNS)
  --dns2 [DNS server IP]         резервный DNS-сервер для первого клиента

Чтобы настроить параметры, вы также можете запустить этот скрипт без аргументов.
```
</details>
