# Raspberry Pi ZERO W

## TODO

[Li-Ion Battery HAT - nakładka do Raspberry Pi - Waveshare 15141](https://elty.pl/pl/p/Li-ion-Battery-HAT-dla-Raspberry-Pi/2817)
[https://botland.com.pl/akumulatory-li-ion/6459-ogniwo-18650-li-ion-sony-us18650vtc4-2100mah-5904422334680.html](https://botland.com.pl/akumulatory-li-ion/6459-ogniwo-18650-li-ion-sony-us18650vtc4-2100mah-5904422334680.html)


## Konfiguracja

1. Instalacja systemu Raspbian

2. Zmiany na karcie sd:

```sh
touch /Volumes/boot/ssh
touch /Volumes/boot/wpa_supplicant.conf
```

Zawartość pliku `wpa_supplicant`:

```sh
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```

3. Logowanie do maszyny:

```sh
ssh pi@raspberry_ip
```

4. Instalacja docker i docker-compose install

[link](https://dev.to/elalemanyo/how-to-install-docker-and-docker-compose-on-raspberry-pi-1mo)

## Konfiguracja OLED Display - Waveshare 13890

<https://www.waveshare.com/wiki/Libraries_Installation_for_RPi>

<https://www.waveshare.com/w/upload/4/46/1.3inch_OLED_HAT_User_Manual_EN.pdf>

<https://stackoverflow.com/questions/48012582/pillow-libopenjp2-so-7-cannot-open-shared-object-file-no-such-file-or-directo>

<https://github.com/rm-hull/luma.examples/issues/24>

<https://pypi.org/project/luma.oled/>

<https://askubuntu.com/questions/1061486/unable-to-locate-package-python-pip-when-trying-to-install-from-fresh-18-04-in>

<https://askubuntu.com/questions/672808/sudo-apt-get-install-python-pip-is-failing>
