# Raspbian

## Konfiguracja wi-fi

Utworzyć plik wpa_supplicant.conf, a w nim zawartość:

```sh
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=PL

network={
    ssid="NAZWA_SIECI"
    psk="HASŁO_SIECI"
}
```

## Logowanie do systemu [headless]

Utworzyć plik `ssh` oraz `wpa_supplicant.conf`:

<https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-headless-raspberry-pi>

## Set up wifi country code from command line

```sh
sudo raspi-config nonint do_wifi_country PL
```

