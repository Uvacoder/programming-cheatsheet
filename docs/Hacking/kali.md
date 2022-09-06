# Kali linux

[The First 10 Things to Do After Installing Kali Linux](https://www.fossmint.com/things-to-do-after-installing-kali-linux/)

[Top 5 things to install](https://techdhee.in/things-to-do-after-installing-kali-linux/#Top_5_Things_to_Do_After_Installing_Kali_Linux)

## The First Things to Do After Installing

### Update, Upgrade, & Dist-Upgrade

```sh
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
# or
sudo apt update && sudo apt -y full-upgrade -y && sudo reboot
```

### Install Tor Browser

```sh
sudo apt install tor
# or
sudo apt-get install tor torbrowser-launcher
# and open by
sudo torbrowser-launcher
```

### Install Software Center

```sh
sudo apt install software-center
```

### Install GDebi Package Manager

Kali comes with dpkg for package management but you could run into issues after installing apps because it doesn’t automatically install apps’ dependencies.

```sh
sudo apt install gdebi
```

### Install VLC Media Player

```sh
sudo apt install vlc
```

## Start vncserver on start up system

<https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-debian-10>

Using `/etc/init.d` I cannot configure service starting automatically. I found the solution which is using `systemd` which is [preferred](https://www.tecmint.com/systemd-replaces-init-in-linux/).

> A init process starts serially i.e., one task starts only after the last task startup was successful and it was loaded in the memory. This often resulted into delayed and long booting time. However, systemd was not designed for speed but for getting the things done neatly which in turns avoid all the UN-necessary delay.

You can easly find how to write those scripts: [here](https://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd)

## Make digitalocean image of kali linux

https://www.kali.org/docs/cloud/digitalocean/

https://medium.com/@hackthebox/how-to-deploy-a-kali-linux-distribution-in-digital-ocean-cloud-c556edf17741
## issues

1. NetworkManager is not working

```sh
sudo systemctl status NetworkManager
sudo systemctl start NetworkManager
```

2. Drivers for tp-link usb

```sh
apt update -y && apt upgrade -y && apt dist-upgrade
sudo apt-get install linux-headers-$(uname -r)
# find header is needed here: http://mirror.internode.on.net/pub/kali/pool/main/l/linux/
```

- Cannot install `linux-headers` package

https://unix.stackexchange.com/questions/328655/cant-install-linux-headers-kali-linux

https://hackersgrid.com/2022/01/install-linux-headers-kali-2022.html

https://github.com/nlkguy/archer-t2u-plus-linux
