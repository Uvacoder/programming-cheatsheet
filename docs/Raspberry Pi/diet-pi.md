# Diet Pi

## Instrukcja instalacji

[link](https://pimylifeup.com/raspberry-pi-dietpi/)

## Headless Install

Żaby połączyć się z rpi zdalnie, po instalacji systemu, trzeba zmienić linię kodu przed pierwszym uruchomieniem:

Plik `dietpi.txt`:

```sh
AUTO_SETUP_NET_WIFI_ENABLED=1
```

Oraz dodać ustawienia sieci w pliku `dietpi-wifi.txt`:

```sh
aWIFI_SSID[0]='network_name'
aWIFI_KEY[0]='network_pass'
```

## Pierwsza konfiguracja serwera domowego

1. Aktualizacja systemu

Wykonywana automatycznie podczas pierwszego logowania do systemu.

2. Instalacja dockera

```sh
curl -fsSL <https://get.docker.com> -o get-docker.sh
sh get-docker.sh
```

3. Instalacja mojego obrazu `micro-network`

```sh
docker pull tullece/micro-network:arm6-latest #or without this command, docker will pull automatically
docker run -d --network host --restart=always tullece/micro-network:arm6-latest
```

## Podstawowe komendy

```sh
dietpi-autostart
dietpi-backup
dietpi-cleaner
dietpi-config
dietpi-cron
dietpi-drive_manager
dietpi-explorer
dietpi-letsencrypt
dietpi-logclear
dietpi-process_tool
dietpi-services
dietpi-software
dietpi-sync
dietpi-update
```

## Rodzaje desktopów

<https://dietpi.com/docs/software/desktop/>
