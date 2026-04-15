[English](README.md) | [简体中文](README-zh.md) | [繁體中文](README-zh-Hant.md) | [Русский](README-ru.md) | [Video en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# Скрипт автоматической установки сервера WireGuard VPN

[![Build Status](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml/badge.svg)](https://github.com/hwdsl2/wireguard-install/actions/workflows/main.yml) [![GitHub Stars](https://img.shields.io/github/stars/hwdsl2/wireguard-install.svg?cacheSeconds=86400&logo=github&style=flat)](https://github.com/hwdsl2/wireguard-install/stargazers) [![License: MIT](docs/images/license.svg)](https://opensource.org/licenses/MIT)

Установщик сервера WireGuard VPN для Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS, Fedora, openSUSE и Raspberry Pi OS.

Этот скрипт позволит вам настроить собственный VPN-сервер всего за несколько минут, даже если вы раньше не использовали WireGuard. [WireGuard](https://www.wireguard.com) — это быстрый и современный VPN, разработанный с упором на простоту использования и высокую производительность.

**Возможности:**

- Полностью автоматическая настройка сервера WireGuard VPN, ввод пользователя не требуется
- Поддержка интерактивной установки с пользовательскими параметрами
- Генерация VPN-профилей для автоматической настройки устройств Windows, macOS, iOS и Android
- Генерация QR-кодов для упрощённой настройки мобильных устройств
- Поддержка управления пользователями WireGuard VPN
- Оптимизация настроек `sysctl` для повышения производительности VPN
- Поддержка двойного стека IPv4 и IPv6 для VPN-клиентов

**Также доступно:**

- Docker VPN: [WireGuard](https://github.com/hwdsl2/docker-wireguard/blob/main/README-ru.md), [OpenVPN](https://github.com/hwdsl2/docker-openvpn/blob/main/README-ru.md), [IPsec VPN](https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/README-ru.md), [Headscale](https://github.com/hwdsl2/docker-headscale/blob/main/README-ru.md)
- Docker ИИ/Аудио: [Whisper (STT)](https://github.com/hwdsl2/docker-whisper/blob/main/README-ru.md), [Kokoro (TTS)](https://github.com/hwdsl2/docker-kokoro/blob/main/README-ru.md), [Embeddings](https://github.com/hwdsl2/docker-embeddings/blob/main/README-ru.md), [LiteLLM](https://github.com/hwdsl2/docker-litellm/blob/main/README-ru.md)
- :book: Книга: [Privacy Tools in the Age of AI](docs/vpn-book.md), [Build Your Own VPN Server](docs/vpn-book.md)

## Установка

Сначала загрузите скрипт на ваш Linux-сервер\*:

```
wget -O wireguard.sh https://get.vpnsetup.net/wg
```

\* Облачный сервер, виртуальный частный сервер (VPS) или выделенный сервер.

**Вариант 1:** Автоматическая установка WireGuard с параметрами по умолчанию.

```
sudo bash wireguard.sh --auto
```

<details>
<summary>
Посмотреть работу скрипта (запись терминала).
</summary>

**Примечание:** Эта запись предназначена только для демонстрационных целей.

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>

**Примечание:** При желании вы можете установить [OpenVPN](https://github.com/hwdsl2/openvpn-install/blob/master/README-ru.md), [IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn/blob/master/README-ru.md) и/или [Headscale](https://github.com/hwdsl2/headscale-install/blob/main/README-ru.md) на тот же сервер.

Для серверов с внешним файрволом (например, [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/firewall/docs/firewalls)) откройте UDP-порт 51820 для VPN.

**Вариант 2:** Интерактивная установка с пользовательскими параметрами.

```
sudo bash wireguard.sh
```

Вы можете настроить следующие параметры: DNS-имя VPN-сервера, UDP-порт, DNS-сервер для VPN-клиентов и имя первого клиента.

Для серверов с внешним файрволом откройте выбранный UDP-порт для VPN.

<details>
<summary>
Нажмите здесь, если не удаётся скачать.
</summary>

Вы также можете использовать `curl` для загрузки:

```
curl -fL -o wireguard.sh https://get.vpnsetup.net/wg
```

Затем следуйте инструкциям выше для установки.

Альтернативные URL для установки:

```
https://github.com/hwdsl2/wireguard-install/raw/master/wireguard-install.sh
https://gitlab.com/hwdsl2/wireguard-install/-/raw/master/wireguard-install.sh
```

Если вы не можете скачать файл, откройте [wireguard-install.sh](wireguard-install.sh), затем нажмите кнопку `Raw` справа. Нажмите `Ctrl/Cmd+A`, чтобы выделить всё, `Ctrl/Cmd+C`, чтобы скопировать, затем вставьте в ваш любимый редактор.
</details>
<details>
<summary>
Дополнительно: автоматическая установка с пользовательскими параметрами.
</summary>

Продвинутые пользователи могут автоматически установить WireGuard с пользовательскими параметрами, указав параметры командной строки при запуске скрипта. Подробнее см. в следующем разделе «просмотр информации об использовании скрипта WireGuard».

В качестве альтернативы можно передать Bash «here document» в качестве входных данных для скрипта установки. Этот метод также можно использовать для передачи входных данных для управления пользователями после установки.

Сначала установите WireGuard в интерактивном режиме с пользовательскими параметрами и запишите все введённые значения.

```
sudo bash wireguard.sh
```

Если вам нужно удалить WireGuard, снова запустите скрипт и выберите соответствующий вариант.

Затем создайте команду установки с пользовательскими параметрами, используя ваши ответы. Пример:

```
sudo bash wireguard.sh <<ANSWERS
n
51820
client
2
y
ANSWERS
```

**Примечание:** Параметры установки могут измениться в будущих версиях скрипта.
</details>
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

## Следующие шаги

После установки вы можете снова запустить скрипт, чтобы управлять пользователями или удалить WireGuard.

Настройте ваш компьютер или устройство для использования VPN. Пожалуйста, обратитесь к следующей инструкции:

**[Настройка клиентов WireGuard VPN](docs/clients.md)**

**Прочитайте [:book: книгу о VPN](docs/vpn-book.md), чтобы получить доступ к [дополнительному контенту](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J).**

Наслаждайтесь собственным VPN! :sparkles::tada::rocket::sparkles:

## Благодарности

Этот скрипт основан на отличной работе [Nyr и участников проекта](https://github.com/Nyr/wireguard-install) с улучшениями и изменениями для совместимости с проектом [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn/blob/master/README-ru.md).

<details>
<summary>
Список улучшений по сравнению с Nyr/wireguard-install.
</summary>

- Улучшена совместимость с Setup IPsec VPN  
- Повышена надёжность скрипта, улучшены ввод и вывод пользователя  
- Поддержка автоматической установки с параметрами по умолчанию или пользовательскими параметрами  
- Поддержка использования DNS-имени в качестве адреса сервера  
- Добавлена поддержка openSUSE Linux  
- Поддержка просмотра списка существующих VPN-клиентов  
- Поддержка отображения QR-кода для клиента  
- Поддержка пользовательских DNS-серверов для VPN-клиентов  
- Поддержка параметров командной строки для управления VPN-клиентами  
- Оптимизация настроек `sysctl` для повышения производительности VPN  
- Улучшено создание файлов конфигурации клиента при использовании `sudo`  

...и многое другое!
</details>

## Лицензия

MIT
