# Linux - tips & tricks

## FAQ

Pobranie server mysql dla precesorów ARM. Nie można pobrać defaultowego systemy od mysql ponieważ nie działa on na raspberry.

```sh
docker run --name mysql-server -e >MYSQL_ROOT_PASSWORD=root -d hypriot/rpi-mysql:5.5
```

#### Doinstalowanie phpmyadmin, aby można było przeglądać w łatwy sposób bazę danych

```sh
docker run --name myadmin -d --link mysql-server:db -p 8080:80 ebspace/armhf-phpmyadmin
```

#### Dodanie nextcloud do dockera. Wybranie katalogu media jako głównego do przrechowywania danych. Katalog media zawiera dysk przenośny

```sh
docker run -d -p 3000:80 -v /media/:/var/www/html/data --name ncloud nextcloud
```

#### Musimy zmienić użytkownika katalogu z poziomu maszyny dockera dla ustalonego katalogu. (than change owner of /var/www/html/data/ in container)

```sh
docker exec rpi-dietpi-main_cloud_1 chown -R www-data:www-data /var/www/html/data/
```

#### Musimy także zmienić uprawnienia do plików z poziomu naszego nadrzędnego hosta. (and add permission to access on host machin

```
sudo chmod u+rwx /mnt/data
```

#### Jak usunąć utworzone wcześniej i zatrzymane konterery

```
docker container prune
```

#### Jak zalogować się do malinki z zewnątrz

- nasz internet musi być widoczny z zewnątrz tzn. musimy posiadać publiczny adres IP
- jeśli publiczny adres IP jest dynamiczny tzn. zmiania się w danym czasie trzeba stworzyć skrypt który będzie aktualizował adres w np. cloudflare zdalnie
- skonfigurować przekierowanie portów na routerze
- domyślnie przy instalacji systemu ```DietPi``` skonfigurowany jest jedynie ```Dropbear``` aby można było połączyć się z zewnątrz zainstaluj ```OpenSSH```

![Zrzut ekranu 2020-03-8 o 22.16.59.png](:storage/0f420367-a031-44cc-a34c-02234e942db1/193a61a9.png)

```
$ dietpi-software
// then choose openssh
```

#### Jak dowiedzieć się więcej o ustawieniach sieciowych

Najlepiej zainstalować jest program o nazwie ```netstat``` jest on dostępny do instalacji przy pomocy komendy: ```apt-get install net-tools```

#### Jeśli występuje problem z logowaniem do ssh

Na początku najlepiej wykonać backup pliku konfiguracyjnego:

```
cp /etc/ssh/blablabla
```

[How to disable ssh password login on Linux to increase security](https://www.cyberciti.biz/faq/how-to-disable-ssh-password-login-on-linux)
Aby możliwe było logowanie przy użyciu kluczy ssh sprawdź: [stackoverflow](https://stackoverflow.com/questions/1556056/permission-denied-publickey-keyboard-interactive)

- sprawdzić czy istnieje plik ```authorized_keys``` w folderze ```/root/.ssh```
- plik musi mieć prawa do użycia ```chmod 600 ~/.ssh/authorized_keys```
- w pliku musi znajdować się klucz publiczny komputera z którego bedziemy się logować

po wprowadzeniu wszystkich poprawek konieczne jest przeładowanie serwisu odpowiedzialnego za ssh

```
service ssh restart
systemctl restart sshd.service
```

#### Żeby zalogować się do serwera potrzebuje wpisywać adres IP

Aby to wyeliminować potrzebujesz zmienić ustawienia ```Proxy status``` w cloudflare na ```DNS only```. W przeciwnym przypadku widoczny jest inny adres IP serwera.

#### run docker container on startup

## MANUALS PAGES

[ssh - sshd_config](http://man.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man5/sshd_config.5?query=sshd_config)

## Komendy

## The best dockers hub

- [teamcity-server](https://hub.docker.com/r/jetbrains/teamcity-server/?ref=login)

### eog

open files

```
# eog image.png
```

#### last | lastlog | lastb

last logged users

```sh
lastlog
last -15
last -F root
lastb -f /var/log/btmp-20190402
```

#### man

program do wyświetlania manuali i przewodników po komendach

```
# man caesar
```

#### top

system processes

```
/* restart ssh service */
$ sudo systemctl restart ssh

/* read file in time */
$ tail -n 500 /var/log/auth.log | grep 'sshd'

/* system logs */
$ journalctl -xe

ps aux - for one window data
kill -9 1047
```

#### top

task manager - table of processes

<https://www.thegeekstuff.com/2010/01/15-practical-unix-linux-top-command-examples/>

#### find

utility that locates files based on user criteria

<https://www.debuntu.org/how-to-find-files-on-your-computer-with-find/index.html>

#### history

```bash
history|awk '{print $2}'|awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c|sort -r
```

#### dpkg

install, remove and provide info about .deb packages

```bash
dpkg -i name_of_the_program
```

#### ifconfig

network interface configuration

```bash
ifconfig wlan0 down | up
```

#### iwconfig

wireless interface configuration

#### diskutil

diskutil podstawowa komenda
diskutil partitionDisk komenda służąca do formatowania dysków
diskutil partitionDisk /dev/disk2 2 FAT32 KALI 50% FAT32 DEBIAN 50% formatowanie pendrive do 2 partycji po 50% miejsca dla każdego

diskutil partitionDisk /dev/disk2 1 MBRFormat "MS-DOS FAT32" EDISON 805.30M

- sudo gives you user right.
- Diskutil calls disk utility program.
- eraseDisk commands to format.
- FAT32 sets the file system.
- MBRFormat tells disk utility to format with a Master Boot Record.
- /dev/disk2 is the location of the USB drive.

#### dnsutils

```bash
apt-get install dnsutils
traceroute google.com nslookup -querytype=soa stackexchange.com
dig google.com
nslookup stackoverflow.com
```

# Linux Commands - Security

bsdgames

#### exiftool

```
# exifftool image.png
```

#### strings

string of image

```
# strings image.png
```

#### file

program do przeglądania plików

```
# file file_name.png
```

#### convert

```
# convert OCR_is_cool.png -scale 300% output.png
```

#### tesseract

program for ocr text from iamges
[Google CTF: Beginner Quest: OCR IS COOL!](https://www.youtube.com/watch?v=j9xht4K-MBk)

```
# apt install tesseract-ocr
# tesseract image.png output
```

#### iwconfig

```bash
/* zmiana mode interfejsu jako monitor mode */
$ iwconfig wlan0 mode monitor

/* uruchomienie monitor mode poprzez specjalny program airmon */
$ airmon-ng start wlan0
```

#### wash / reaver

wash - to program który pomaga nam wyszukać sieci, jakie posiadają zabezpieczenie WPS, które łatwo jest zhakować.

Wash is a utility for identifying WPS enabled access points. Wash is included in the Reaver package.

```bash
wash -i wlan0
```

reaver - program do łamania zabezpieczeń WPS, wersja 1.6.5 posiada pewną wadę która uniemożliwia wykonanie tej czynności dlatego lepiej zaopatrzyć się w wersję 1.6.1

```bash
reaver -i wlan0 -b FC:2D:5E:1D:52:C4 -c 1 -vvv
```

jeśli używamy reaver to potrzebujemy w tle wysyłać requesty o to aby nie ignorował ich, możemy do tego celu użyć tej komendy:
aireplay-ng --fakeauth 30 -a FC:2D:5E:1D:52:C4 -h 52-61-D4-D6-3B-30 0

#### airodump-ng - packet sniffing, wireless packet capture tool

used  for  packet  capturing of raw 802.11 frames for the intent of using them with aircrack-ng

```bash
airodump-ng —band abg mon0
airodump-ng —bssid F8:F2:F8:F2:F8:F2 —channel 2 —write test mon0

/* skanowanie dokładnego ssid i zapis do pliku danych które otwieramy w wireshark */
aireplay-ng --deauth 10000000000 -a D8:D7:75:21:CC:64 -c 14:C2:13:BB:76:06 -D wlan0
```

#### airmon-ng

POSIX sh script designed to turn wireless cards into monitor mode.

airmon-ng <start|stop> <interface> [channel] airmon-ng <check> [kill]

<https://unix.stackexchange.com/questions/223625/cannot-connect-to-internet-after-using-airmon-ng-check-kill>

airmon-ng pokazuje interfejsy sieciowe podłączone do komputera
airmon-ng check kill zabija wszystkie procesy związane z połączeniami internetowymi
airmon-ng start wlan0 uruchomienie monitor mode poprzez specjalny program

#### aireplay-ng

inject packets into a wireless network to generate, is used to inject/replay frames.  The primary function is to generate traffic for the later use in aircrack-ng for cracking the WEP and WPA-PSK keys. are different attacks which can cause deauthentications for the purpose of capturing WPA handshake data, fake authentications, Interactive packet replay,  hand- ARP request injection and ARP-request reinjection. With the packetforge-ng tool it's possible to create arbitrary frames.

aireplay-ng [options] <replay interface>

aireplay-ng —deauth 100000000 -a F8:F2:F8:F2:F8:F2 -c F8:F2:F8:F2:F8:F2 mon0 wysyłanie fakowych pakietów danych które rozłączą maszynę od internetu imitując taką chęć oraz podrabiając numer MAC tego hosta i wysyłaniu tego do routera

    Where to put - in progress

Linux From Scratch (LFS) is a project that provides you with step-by-step instructions for building your own customized Linux system entirely from source.
> <http://www.linuxfromscratch.org/lfs/>

Laboratory:

- Phone with android -> flash memory to pwnix <https://wiki.pwnieexpress.com>
- Pendrive with Kali Linux
- Network card tplink
- Router with soft OpenWRT

<https://youtu.be/0Z9eBvDmi9I>
<https://youtu.be/24HpS4Po6LE>

Identify your external USB with diskutil - the disk ID (disk2, disk3 etc is represented as <DISK> below):
$ diskutil list
If necessary, prep the external USB with diskutil to get a single partition:
$ diskutil eraseDisk FAT32 KALI /dev/<DISK>
Unmount the volume in DIsk Utility, or at the command-line:
$ diskutil unmountDisk /dev/<DISK>
Then use dd to make a bootable image on the USB:
$ sudo dd if=<path to downloaded .iso> of=/dev/<DISK> bs=1m

- Na pendrive
diskutil list            - pokazuje listę dysków podłączonych do komputera
diskutil unmountDisk /dev/diskX        - odmontowanie dysku o numerze X z komputera aby zainstalować linuxa
cd /path/toLinux           - przejście do odpowiedniego katalogu z obrazem ISO linuxa
sudo dd if=kali-linux-XXX-amd64.iso of=/dev/diskX bs=1m   - wypalenie wersji linuxa na pendrive

You can view connections using that port with
netstat -ntpl|grep -i 9418

# Security information

### Couldn't get pcap handle, exiting

```
wash -i wlan0
```

- this is a problem with wi-fi card
- [x] ERROR: pcap_activate status -1
- [x] PCAP: generic error code

### When aireplay-ng doesn't work correctly

<https://security.stackexchange.com/questions/72518/wifi-penetration-testing-why-aireplay-ng-de-authentication-does-not-work>
I had a similar problem with an RTL8812AU on Kali 2018. What fixed it for me was throwing a -D into the attack command line so it stops trying to automatically determine the channel and just does what you tell it to.

## Links

Przydatne linki

- RFID clonned
<https://www.youtube.com/watch?v=IHyM7o-OVqA>

- Vulnhub
<https://www.vulnhub.com/>

- Dziwny pendrive
<https://shop.hak5.org/products/usb-rubber-ducky-deluxe>

/usr/local/bin/node
/media/rpi-dietpi-main/scripts

PORT NUMBERS
<https://www.utilizewindows.com/list-of-common-network-port-numbers/>

NETWORK TERMINOLOGY
<https://www.digitalocean.com/community/tutorials/an-introduction-to-networking-terminology-interfaces-and-protocols>

KALI DRIVERS FOR TL-WN722N

<https://www.youtube.com/watch?v=NhHiXzqkx_s>
[Download and Installation]

apt update && apt upgrade
apt install -y bc linux-headers-amd64
git clone <https://github.com/kimocoder/rtl8188eus>
cd rtl8188eus
cp realtek_blacklist.conf /etc/modprobe.d
make
make install

[Enabling Monitor Mode]

systemctl stop NetworkManager.service
iwconfig wlan0 mode monitor
airodump-ng wlan0

[Testing Packet Injection]

aireplay-ng --test wlan0
