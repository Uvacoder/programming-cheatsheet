---
sidebar_position: 1
---

# General

[usefull snipets](https://snippets.khromov.se/)

## The Linux Directory Structure

- `/bin` binaries - programs or applications (cat, ls, cp)
- `/sbin` system binaries
- `/boot` - bootloader, everything what system needs to start running
- `/dev` - where devices lives,
  - `/char`
  - `/sda` - sda1, sda2
- `/etc` - storing configuration (sources.list, cron, application settings)
- `/home` - contains users home folders, for personal files and documents
- `/lib` - libraries
- `/media` - usually systems mount drivers automaticaly here (pendrives, cdroms)
- `/mnt` mount - folder to mount manually all drivers (pendrives, cdroms, network drives)
- `/opt` optional - folder to manual install software (virtualbox, printer software)
- `/proc` - sudo files, for system processes
- `/root` - root user home folder
- `/run` - tempfs files system, files to faster start system
- `/snap`
- `/srv` - service directory (ftp server, http server)
- `/sys` system - similar to `/run` directory, installed during the boot start system
- `/tmp` temporary - temporary director for programs during session, you can recover something from there
- `/usr` user - user applications
  - `/local`
  - `/src`
  - `/share`
- `/var` - variable directory
  - `/crash`
  - `/logs` for system and any diffrent applications

## Graphic interfaces

HOW COMPUTER WORKS?
DIFFERENCE 32 and 64 bits.

Every distro can take another GUI:

- Unity (default for ubuntu)
- Xfce (default for kali)
- Gnome
- KDE
- KDE Plasma
- LXDE
- Cinnamon
- MATE

[DesktopEnvironment - Debian Wiki](https://wiki.debian.org/DesktopEnvironment)

amd64 is 64-bit
i386 is 32-bit

FAT32 format can only takes uppercases names.

## How to check public and private address IP

The following commands will get you the IP address list to find public IP addresses for your machine:

curl ifconfig.me
curl -4/-6 icanhazip.com
curl ipinfo.io/ip
curl api.ipify.org
curl checkip.dyndns.org
dig +short myip.opendns.com @resolver1.opendns.com
host myip.opendns.com resolver1.opendns.com
curl ident.me
curl bot.whatismyipaddress.com
curl ipecho.net/plain
The following commands will get you the private IP address of your interfaces:

ifconfig -a
ip addr (ip a)
hostname -I | awk '{print $1}'
ip route get 1.2.3.4 | awk '{print $7}'
(Fedora) Wifi-Settings→ click the setting icon next to the Wifi name that you are connected to → Ipv4 and Ipv6 both can be seen
nmcli -p device show

## How to check using DNS Server

```sh
https://www.whatsmydnsserver.com/
```

## How to check current user

```sh
# login name
whoami
echo $USER
# or full information
id
# or user name
id -F
# rest of user checkers
id -u  # returns UID
id -un # returns username
id -g  # returns primary (a.k.a. effictive) GID
id -gn # returns primary Group Name
# or currently logged users to system
w
```

## How to check sum of file

```sh
md5 /path/to/file
shasum -a 1 /path/to/file
shasum -a 256 /path/to/file
shasum -a 512 /path/to/file
```

## How to list all files in catalog with sort by date

```sh
ls -haltr
# human readable size
# showing all dot prefixes
# list files
# sort by time
# revert results
```

## How to make public ssh key required on log in process

[link digitalocean](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)

## How to merge two or more mp3 files

```sh
cat file1.mp3 > newfile.mp3
cat file1.mp3 file2.mp3 file3.mp3 > newfile.mp3
```

> Only if MP3 files are recorded at the same bitrate.

## Envs

echo $SHELL
echo #ZSH

## xargs - Using subshell with xargs and docker

> Returned text from first execution will be passed to the second command

```bash
docker images artifactory.mrgreen.tech/docker/gametek/sportsbook/sb-mfe:latest -q | xargs docker stop
```

## Update grub

```bash
sudo update-grub
```

## Manage users and privilages

```bash
-rw-r--r--@  1 kubek  staff  20484 Oct 18 15:28 some_file.txt
drwxr-xr-x  19 kubek  staff    608 Oct 18 15:28 some_folder
```

First letter says about `-` file or `d` folder (directory). Next are tell us about access to this specific file/folder.

| # |        Permission       | rwx | Binary |
|:-:|:-----------------------:|:---:|:------:|
| 7 | read, write and execute | rwx | 111    |
| 6 | read and write          | rw- | 110    |
| 5 | read and execute        | r-x | 101    |
| 4 | read only               | r-- | 100    |
| 3 | write and execute       | -wx | 011    |
| 2 | write only              | -w- | 010    |
| 1 | execute only            | --x | 001    |
| 0 | none                    | --- | 000    |

You can modify access using command `chmod`, fe.

```bash
chmod 0664 sharedFile
```

## Zip/Unzip files

```bash
zip -r filename.zip /home/folder/*
unzip html.zip -d html/
mv ./html/* /home/dazdyqephu/domains/ohsospecial.nl/public_html/
```s

## Commands

```bash
adduser [user name] #add new user to the system
cat /etc/passwd #show users
cat /etc/shadow #show users and passwords
su [user-name] #switch to provided user
```

## Read more

[Shadow Passwords](https://www.cyberciti.biz/faq/understanding-etcshadow-file)
[Crack users passwords](https://null-byte.wonderhowto.com/how-to/crack-shadow-hashes-after-getting-root-linux-system-0186386/)

## Manage networks

```bash
ifconfig #shows you network interfaces available for you
iwconfig #shows you only wireless adapters
ping [server-ip-address]
arp -a
netstat -ano #shows you connections which are running on you machine
router #shows you routing table - where you traffic is exit essentially
```

## Manage files (create|modify|remove)

```bash
nano new-file.txt
touch new-file.txt
gedit new-file.txt
```

## Add text to file or overwrite file by text

```sh
echo "tekst" > new-file.txt #create file and override with text
echo "tekst" >> new-file.txt #create file and save text at the bottom of file
```

## Manage services (start|stop)

```bash
service apache2 start #start apache server
python -m SimpleHTTPServer 80 #run python server which is smiler than apatche and can be run in every folder
systemctl enable postgresq #run for example postgres database not only fot that session but also after reboot machine
```

## How to find files matched to pattern

```sh
find . -name "*edit*"
```

## How to remove found files

```sh
find . -name "*edit*" -delete
# OR
find . -name "*edit*" -exec rm -rf {} \;
```

## How to save command results in file

```sh
find . -name "*edit*" >> filename.txt
```

## Check current shell / Change shell

```sh
# Check current shell:
echo $SHELL
# or
echo $0
# or
ps

# Possible installed shells:
cat /etc/shells

# Change the default shell to Bash by running the following command:
chsh -s /bin/bash
# or
chsh -s /bin/zsh
# or
chsh -s $(which zsh)
```

## How to save logs and watch/browse loglevel

```sh
# watch
tail -f /var/log/cups/error_log
```

## How to set up more informations in logs

```sh
debug2 – Log everything.
debug – Log almost everything.
info – Log all requests and state changes.
warn – Log errors and warnings.
error – Log only errors.
none – Log nothing.
```

## How to mangage servuces like systemctl (start/restart/status/stop)

Examples:

```bash
service apache2 start #start apache server
python -m SimpleHTTPServer 80 #run python server which is smiler than apatche and can be run in every folder
systemctl enable postgresq #run for example postgres database not only fot that session but also after reboot machine
```

## How to debug systemctl

```sh
# With any issues with systemctl run:
journalctl -xe
# or for example:
systemctl status hostapd.service
```

## How to restart service

```sh
service cups restart
# or
sudo /etc/init.d/cupsys restart
# or
sudo systemctl restart cups
sudo systemctl restart cupsys
```

## Run script directly from the Internet

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# or
wget https://raw.githubusercontent.com/lemariva/wifi-cups-server/master/rpi-cup-server.sh
chmod +x rpi-cup-server.sh
./rpi-cup-server.sh
```

## Check status of service

```sh
service avahi-daemon status
```

## Reboot the machine

```sh
sudo reboot
# or
sudo shutdown -h now
# or
sudo shutdown -r now
# or
sudo shutdown -r 10 # after 10 minutes
# or
sudo init 6
# or (does not need any filesystem access):
echo b > /proc/sysrq-trigger
```

## Shutdown the machine

```sh
shutdown #turn off machine after in one minute
shutdown -h now
```

## Add new user | change password

```sh
adduser name_of_user
passwd name_of_user
# or root pass:
passwd
```

## How to configure Wake on LAN

[javascript](https://github.com/agnat/node_wake_on_lan)

1. Turn on option in BIOS

<https://pl.if-koubou.com/articles/how-to/what-is-wake-on-lan-and-how-do-i-enable-it.html>

2. Turn on option for network card in system (I did it in kali linux)

3. Make a request using npm package

<https://www.npmjs.com/package/wol>

```sh
sudo apt-get install ethtool
sudo ethtool eth0
sudo ethtool -s eth0 wol g
```

## How to automatically run program on Linux startup

<https://www.simplified.guide/linux/automatically-run-program-on-startup>

<https://www.baeldung.com/linux/run-script-on-startup>

- Using init.d
- Manage using systemd
- Create a cron job
- Run using rc.local

## Copy directory with all nested files

```sh
cp -R path_to_source path_to_destination/

```

- -R means copy directories recursively. You can also use -r since it's case-insensitive.

## Run script for initial boot up from sd card `cmdline.txt` file

<https://forums.raspberrypi.com/viewtopic.php?t=308257>

Important commands: `systemd.run` `init`.

```sh
console=serial0,115200 console=tty1 root=PARTUUID=83c4223d-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet init=/usr/lib/raspi-config/init_resize.sh systemd.run=/boot/firstrun.sh systemd.run_success_action=reboot systemd.unit=kernel-command-line.target
```

## Copy data from/to remote server

For better performance you can use `rsync` or archive files and copy only one file.

Copy file from a remote host to local host SCP example:

```sh
scp username@from_host:file.txt /local/directory/
```

Copy file from local host to a remote host SCP example:

```sh
scp file.txt username@to_host:/remote/directory/
```

Copy directory from a remote host to local host SCP example:

```sh
scp -r username@from_host:/remote/directory/  /local/directory/
```

Copy directory from local host to a remote hos SCP example:

```sh
scp -r /local/directory/ username@to_host:/remote/directory/
```

Copy file from remote host to remote host SCP example:

```sh
scp username@from_host:/remote/directory/file.txt username@to_host:/remote/directory/
```

- –r Recursively copy entire directories. Note that this follows symbolic links encountered in the tree traversal.
- -C Compression enable. Passes the -C flag to ssh to enable compression.
- -l limit – Limits the used bandwidth, specified in Kbit/s.
- -o ssh_option – Can be used to pass options to ssh in the format used in ssh_config.
- -P port – Specifies the port to connect to on the remote host. Note that this option is written with a capital ‘P.’
- -p Preserves modification times, access times, and modes from the original file.
- -q Quiet mode: disables the progress meter as well as warning and diagnostic messages from ssh.
- -v Verbose mode. Print debugging messages about progress. This is helpful in debugging connection, authentication, and configuration problems.

## Archive file into .zip and unarchive them

<https://linuxize.com/post/how-to-zip-files-and-directories-in-linux/>

<https://linuxize.com/post/how-to-unzip-files-in-linux>

## Uprawnienia dostępu `chmod`

<https://pl.wikipedia.org/wiki/Chmod>

<http://www.chmod.pl/>

Cyfra Prawa Litera Binarnie
0 Brak praw --- 000
1 Wykonywanie --x 001
2 Zapis -w- 010
3 Zapis i wykonanie -wx 011
4 Odczyt r-- 100
5 Odczyt i wykonanie r-x 101
6 Odczyt i zapis rw- 110
7 Odczyt, zapis i wykonanie rwx 111

## Show open ports | kill processes which are blocking ports

> kill -15 gives the process a chance to clean up after itself.

```bash
netstat -lptn
# or
sudo lsof -i :3000
# or
netstat --tcp --listening --programs --numeric
# and
kill -9 <PID>
```

## Show all running processes in Linux

```sh
ps aux
```

## Show HTTP headers using curl

```sh
curl -I google.com
```

## View open internet connections and the programs using them

```sh
netstat -naptu
```

## How to check temperature on linux system

```sh
sensors
# or
hardinfo #Package which install graphical interface with every information about system
hardinfo -rma devices.so
```

## Manage users - add user / remove user

Instead of using `useradd` better choose `adduser`, but if you decide to use first option remember about adding special parameter `-d` which will create all of required by user folders in `/home` directory.

```sh
adduser {username}
userdel -r {username}

passwd jsmith #create password for created user
```

## Add user to group

<https://linuxize.com/post/how-to-add-user-to-group-in-linux/>

```sh
groups #show all possible groups
less /etc/group

usermod -a -G group1,group2,group3 {username}
```

## Log out different user

<https://www.cyberciti.biz/faq/linux-logout-user-howto/>

```sh
pkill -KILL -u {username}
```

## Run script on system startup

<https://linuxhint.com/use-etc-rc-local-boot/>
<https://unix.stackexchange.com/questions/49626/purpose-and-typical-usage-of-etc-rc-local>

- Edit `sudo nano /etc/rc.local` file and add permissions to it `sudo chmod +x /etc/rc.local`

> Add terminal commands here without sudo

```sh
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Ensure that the script will "exit 0" on success or any other
# value on error.
#
# To enable or disable this script, just change the execution
# bits.
#
# By default, this script does nothing.

exit 0
```

- Few more things:

```sh
sudo systemctl enable rc-local
systemctl start rc-local.service
systemctl status rc-local.service
```

## Connect to wifi on debian machine

```sh
# Add settings to file:
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
# Restart service to run wifi connection:
sudo wpa_cli -i wlan0 reconfigure
```

## Show system information | Processor type | Processor name | System information | hardware information

```sh
uname -m
# or every informations:
uname -a
```

## Find the OS/Arch of you system | OS name | Linux version | Check the linux distribution

```sh
cat /etc/*release
# or
cat /etc/os-release
# or
cat /proc/version

# Maybe install first: apt-get -y install lsb-core
lsb_release -d
# or
lsb_release -a
```

## How to mount usb drive/device

```sh
fdisk -l
# or
lsblk -l

mkdir /media/folder_name
chmod 777 /media/folder_name
mount /dev/sdb1 /media/folder_name
```

## How to install GUI

```sh
apt-get install gdm3
# or
apt-get install gnome

# If your installation starts up to a command line, enter the command “startx”. If this results in a
# command not found message, install the desktop GUI by running “apt install kali-linux-full” or “apt
# install gnome gdm3” then editing your .xinitrc file and add the line “exec startx”.
```

## Find networks

```sh
sudo iwlist wlan0 scan | grep ESSID
```

## Devices

```sh
lsusb -v -d 0cf3:9271
idVendor=0cf3
cidProduct=9271
```

## Error with NO_PUBKEY during apt-get install

```sh
# The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B7E65990E879472F

sudo apt-get --allow-unauthenticated update
```

## Configure static IP Address

[Link](https://linuxhint.com/configure-static-ip-address/)

```sh
ip addr
sudo nano
sudo systemctl restart network-manager.service
```

## Cannot log into ssh

```sh
# Ssh is not working

sudo service ssh status
sudo service ssh start
```

## How to check if port is open

```sh
telnet www.synology.com 1723
```

## WWW Servers

- [lighttpd](https://www.lighttpd.net/)
- [nginx](https://www.nginx.com/)
- [apache](https://httpd.apache.org/)

## Proxmox

[WIKI](https://pve.proxmox.com/wiki/Convert_Debian_CT_to_Kali)

[Proxmox configuration](https://www.youtube.com/watch?v=2foI-hP1omA&t=1128s)

[Windows installation](https://www.youtube.com/watch?v=6c-6xBkD2J4)

## How to turn off/turn on wifi interfaces

```sh
# https://raspberrytips.com/disable-wifi-raspberry-pi/
sudo ip link set wlan0 down
sudo ip link set wlan0 up
# or
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

## How to change default version of installed python

<https://www.safe.security/assets/img/research-paper/pdf/A%20Beginners%20Guide%20to%20Linux%20firewall.pdf>

```sh
# show current version
npm config get python
echo $PYTHON
# change to new version
npm config set python python3
export PYTHON=python3
## Administration of iptables firewall
```

```sh
# Save to file
iptables-save > /etc/iptables/rules.v4

# Restore data
iptables-restore < /etc/iptables/rules.v4

# Firewall rules save
iptables-persistent
/etc/iptables/rules.v4
```

## Run node script in crontab - node process continuously

https://www.digitalocean.com/community/tutorials/nodejs-cron-jobs-by-examples

https://www.npmjs.com/package/node-cron

Edit `crontab -e` and add there:

```sh
*/30 * * * * /usr/local/bin/node /home/example/script.js
```

JS code will be executing every 30 minutes.

## How to log in using `ssh` with password

https://www.digitalocean.com/community/questions/enable-both-password-and-key-file-to-ssh-logon-in

