---
sidebar_position: 1
---

# General

This topic covers informations about Raspberry Pi platform, describing process of learn, issues and solutions for a specific areas.

[raspberry-valley](https://raspberry-valley.azurewebsites.net/)

[awesome-raspberry-pi](https://project-awesome.org/thibmaek/awesome-raspberry-pi)

## Raspberry PI

- Raspberry PI Pico - 0.006 W - 0.33 W (max)
- Raspberry PI Zero - 0.4 W (idle)
- Raspberry PI 3 B+ - 1.9 W (idle)
- Raspberry PI 4 B 8GB - 2.7 W (idle)

[Models](https://socialcompare.com/en/comparison/raspberrypi-models-comparison)
[Power Consumption](http://www.pidramble.com/wiki/benchmarks/power-consumption)
[Power Consumption 2](https://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-zero-conserve-energy)
[Overclock SD Card Speed](http://www.pidramble.com/wiki/benchmarks/microsd-cards)

## Default Linux Passwords | Domyślne hasła loginy linux

Raspberry Pi Distributions Username Password
Raspberry Pi OS pi raspberry
DietPi root dietpi
Lakka Linux root root
Kali Linux old root toor
Kali Linux new kali kali
OpenELEC root openelec
Arch Linux ARM root root
Debian pi raspberry
LibreELEC root libreelec
OSMC osmc osmc
QtonPi root rootme
Ubuntu Server ubuntu ubuntu
ROKOS rokos rokos
Retropie pi raspberry

## Online emulator

<https://wokwi.com/arduino/projects/300210834979684872>

## Versions

- Raspberry PI Pico - 0.006 W - 0.33 W (max)
- Raspberry PI Zero - 0.4 W (idle)
- Raspberry PI 3 B+ - 1.9 W (idle)
- Raspberry PI 4 B 8GB - 2.7 W (idle)

[Models](https://socialcompare.com/en/comparison/raspberrypi-models-comparison)
[Power Consumption](http://www.pidramble.com/wiki/benchmarks/power-consumption)
[Power Consumption 2](https://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-zero-conserve-energy)
[Overclock SD Card Speed](http://www.pidramble.com/wiki/benchmarks/microsd-cards)

## Power consumption

Pi Model Pi State Power Consumption
A+ Idle, HDMI disabled, LED disabled 80 mA (0.4W)
A+ Idle, HDMI disabled, LED disabled, USB WiFi adapter 160 mA (0.8W)
B+ Idle, HDMI disabled, LED disabled 180 mA (0.9W)
B+ Idle, HDMI disabled, LED disabled, USB WiFi adapter 220 mA (1.1W)
model 2 B Idle, HDMI disabled, LED disabled 200 mA (1.0W)
model 2 B Idle, HDMI disabled, LED disabled, USB WiFi adapter 240 mA (1.2W)
Zero Idle, HDMI disabled, LED disabled 80 mA (0.4W)
Zero Idle, HDMI disabled, LED disabled, USB WiFi adapter 120 mA (0.7W)

## Operation system

It was a huge story to choose the best one. Kali linux is working very slow on Raspberry Pi 3 B+. Raspberry Pi OS (before Raspbian) in the biggest option is also not so fast. I prefer DietPi.

<https://www.kali.org/get-kali/#kali-arm>
<https://www.raspberrypi.com/software/operating-systems/>
<https://dietpi.com/>
<https://retropie.org.uk/download/>

## Overclocking

Raspberry Pi 3 B+ ma już na starcie bardzo wysoko podkręcony procesor i ram. Żeby móc dalej podnosić szybkość najlepiej kupić obudowę z wiatrakiem. Polecana jest `iUniker Raspberry Pi 3 B+ Case` lub w całości aluminiowa dostępna na aliexpress.

Bezpieczna temperatura maksymalna procesora wynosi ok. 85 stopni C i można ją zadeklarować w `config.txt` jako pole `temp_limit=85`.

Do pomiaru temperatury używamy `vcgencmd` tutaj: [link jak zainstalować](https://pypi.org/project/vcgencmd/).

```sh
/opt/vc/bin/vcgencmd measure_temp
# lub
vcgencmd measure_temp
# lub
while true ; do vcgencmd measure_temp ; sleep 1 ; done
```

możemy utworzyć sobie alias `temp` zapisując `alias temp='/opt/vc/bin/vcgencmd measure_temp'` w pliku `nano /home/pi/.bash_aliases`.

W folderze `/sys/devices/system/cpu/cpu0/cpufreq/` można odczytywać informację o szybkości działania poszczególnych rdzeni procesora.

`cpuinfo_min_freq` — is the minimum frequency for the “idle” mode

`cpuinfo_max_freq` — is the maximum frequency

`cpuinfo_cur_freq` — is the current running frequency of Raspberry Pi

The default CPU configuration for the Raspberry Pi board, which goes in idle mode with no task is the following:

arm_freq=600MHz
core_freq=250MHz

If processes are running, the frequency goes up to:

arm_freq=1200
core_freq=400 (which is the maximum default values for the Raspberry PI 3).

Performance test:

```sh
sysbench --test=memory --cpu-max-prime=2000 --num-threads=4 run
```

Pomiar prędkości procesora:

```sh
watch -n 1 vcgencmd measure_clock arm
```

[more info](https://medium.com/@software_news/how-to-overclock-raspberry-pi-3-50658b7c6044)

## How to manage Kali Linux on Raspberry Pi

[configuration](https://gbhackers.com/raspberry-pi-and-kali-linux/)

## Konfiguracja serwera drukarki/wydruku | [print,server,printer]

[link](http://uczymy.edu.pl/wp/blog/2017/11/10/serwer-wydruku-raspberry-pi-zero-cups/)

## How to install kali linux without external monitor

[headless kali linux](https://github.com/staxth/headless-kali-pi)

## How to manage Kali Linux on Raspberry Pi

[configuration](https://gbhackers.com/raspberry-pi-and-kali-linux/)
