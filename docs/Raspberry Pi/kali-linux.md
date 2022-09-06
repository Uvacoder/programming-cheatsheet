# Kali linux

https://computerpry.blogspot.com/2022/02/how-to-connect-tp-link-ac600-wifi-adapter-with-kali-linux.html

https://morfikov.github.io/post/recenzja-karta-wifi-tp-link-archer-t4u/

https://morfikov.github.io/post/recenzja-karta-wifi-tp-link-tl-wn722n/

https://morfikov.github.io/post/konfiguracja-trybu-ap-kart-wifi-na-debianie/

https://morfikov.github.io/post/jak-ukryc-nazwe-sieci-wifi-essid-przed-wigle-net-google-mozilla/

https://morfikov.github.io/post/metadane-plikow-graficznych-exif/

https://morfikov.github.io/post/jak-zaszyfrowac-raspberry-pi-raspios-raspbian-luks/



## VNC | share screen to different machines

<https://medium.com/@TheNeelOfficial/headless-kali-linux-in-a-raspberry-pi-9e54c16c2475>

<https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04>

```sh
vncserver :1 -geometry 1920x1080 -depth 24 #RUN
vncserver -kill :1 #KILL
```

<https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04>

Open server: `vnc://machine_ip:5901` or 5902, etc.

Alternatives:

- Kali In The Browser (noVNC)

> Using novnc x11vnc packages

<https://www.kali.org/docs/general-use/novnc-kali-in-browser/>

- Kali In The Browser (Guacamole)

<https://www.kali.org/docs/general-use/guacamole-kali-in-browser/>

## How to set up LCD 3.5" MPI3508

Used system `kali-linux-2021.3-rpi4-nexmon-arm64.img.xz`

1. Install kali on sd card using `balenaEtcher`
2. Create backup of config.txt file `sudo cp /boot/config.txt /boot/config.txt.bk`
3. Run kali (l: kali, p: kali) and connect with the Internet
4. Clone repo `git clone https://github.com/lcdwiki/LCD-show-kali`
5. Run command `cd LCD-show-kali && sudo ./LCD35-show`

- now RPi will reboot and show kernel error

1. Open SD card on the different computer and copy and replace code from `config.txt.bk` to `/boot/config.txt` without last section, which should be like this:

```
... rest of code from config.txt ...

# If you would like to enable USB booting on your Pi, uncomment the following line.
# Boot from microsd card with it, then reboot.
# Don't forget to comment this back out after using, especially if you plan to use
# sdcard with multiple machines!
# NOTE: This ONLY works with the Raspberry Pi 3+
#program_usb_boot_mode=1
hdmi_force_hotplug=1
dtparam=i2c_arm=on
dtparam=spi=on
enable_uart=1
dtoverlay=tft35a:rotate=270
```

7. Update packages `apt update`

- now rpi should works with TFT LCD 3.5

8. Instalal package for calibration `apt-get install xinput-calibrator`.
9. Edit file `sudo nano /etc/X11/xorg.conf.d/99-calibration.conf` with configuration:

```
Section "InputClass"
    Identifier      "calibration"
    MatchProduct    "ADS7846 Touchscreen"
    Option  "Calibration"   "160 3723 3896 181"
 Option  "SwapAxes" "1"
 Option "TransformationMatrix"  "1 0 0 0 -1 1 0 0 1"
EndSection
```

10. Reboot system by: `reboot` command and be happy with your kali linux on LCD.

- To calibrate touch screen run command `xinput-calibrator`

- If you want back to HDMI connection run script `cd LCD-show-kali && sudo ./LCD35-show`

### FILES

[LCD drivers for kali](https://github.com/lcdwiki/LCD-show-kali)

[LCD wiki](http://www.lcdwiki.com/3.5inch_RPi_Display)

[LCD manual](https://www.cedelettronica.com/documents/e2a2d148-c375-428b-8967-e431a3b949a6)

### Default config.txt kali linux file for RPi 3 B+

```
# For more options and information see
# http://rpf.io/configtxt
# Some settings may impact device functionality. See link above for details

# uncomment if you get no picture on HDMI for a default "safe" mode
#hdmi_safe=1

# uncomment this if your display has a black border of unused pixels visible
# and your display can output without overscan
#disable_overscan=1

# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
#overscan_left=16
#overscan_right=16
#overscan_top=16
#overscan_bottom=16

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
#hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
#hdmi_group=1
#hdmi_mode=1

# uncomment to force a HDMI mode rather than DVI. This can make audio work in
# DMT (computer monitor) modes
#hdmi_drive=2

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=4

# uncomment for composite PAL
#sdtv_mode=2

#uncomment to overclock the arm. 700 MHz is the default.
#arm_freq=800

# Uncomment some or all of these to enable the optional hardware interfaces
#dtparam=i2c_arm=on
#dtparam=i2s=on
#dtparam=spi=on

# Uncomment this to enable infrared communication.
#dtoverlay=gpio-ir,gpio_pin=17
#dtoverlay=gpio-ir-tx,gpio_pin=18

# Additional overlays and parameters are documented /boot/overlays/README

# Enable audio (loads snd_bcm2835)
dtparam=audio=on

# USB mass storage boot is available on Raspberry Pi 2B v1.2, 3A+, 3B, and 3B+ only.
#program_usb_boot_mode=1

[pi2]
# Pi2 is 64bit only on v1.2+
# 64bit kernel for Raspberry Pi 2 is called kernel8 (armv8a)
kernel=kernel8-alt.img
[pi3]
# 64bit kernel for Raspberry Pi 3 is called kernel8 (armv8a)
kernel=kernel8-alt.img
[pi4]
# Enable DRM VC4 V3D driver on top of the dispmanx display stack
#dtoverlay=vc4-fkms-v3d
#max_framebuffers=2
# 64bit kernel for Raspberry Pi 4 is called kernel8l (armv8a)
kernel=kernel8l-alt.img
[all]
#dtoverlay=vc4-fkms-v3d
# Tell firmware to go 64bit mode.
arm_64bit=1
```

## Hacking

Konfiguracja nowe instancji KALI na Raspberry Pi

> Nie da się definitywnie uruchomić wifi w trybie headless dopóki ten task nie zostanie rozwiązany: [link](https://gitlab.com/kalilinux/build-scripts/kali-arm/-/issues/255). Pewnie można zrobić swój build systemu i wypalić go na karcie, ale wymaga to 8GB ramu jest opisane [tutaj](https://gitlab.com/kalilinux/build-scripts/kali-arm#building).

Nie udało mi się po 2 dniach prób uruchomić wi-fi przy inicjalizacji urządzenia. Sposobem aby to zrobić jest plik wpa_supplicant.conf, który trzeba dodać do karty sd przed pierwszym uruchomieniem. W moim przypadku dla Kali to nie działa. Żeby to ominąć można podłączyć się przez kabel lub przy pomocy zew. monitora zalogować do sieci.

Być może jest to powiązane z ustawieniem `coutry`, które definiuje jakie częstotliwości mogą być obsługiwane przez router.

[Headless Kali Linux in a Raspberry Pi](https://medium.com/@TheNeelOfficial/headless-kali-linux-in-a-raspberry-pi-9e54c16c2475)

[https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf](https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf)

[https://charlesreid1.com/wiki/Kali_Raspberry_Pi/Headless](https://charlesreid1.com/wiki/Kali_Raspberry_Pi/Headless)

[https://www.raspberrypi-spy.co.uk/2017/04/manually-setting-up-pi-wifi-using-wpa_supplicant-conf/](https://www.raspberrypi-spy.co.uk/2017/04/manually-setting-up-pi-wifi-using-wpa_supplicant-conf/)

[https://www.hackster.io/Ladvien/setup-headless-wifi-on-re4son-s-kali-pi-2cf12b](https://www.hackster.io/Ladvien/setup-headless-wifi-on-re4son-s-kali-pi-2cf12b)

Żeby dostać się do urządzenia wpisujemy: `ssh kali@ip_address` hasło `kali`.

[https://ladvien.com/kali-pi-headless-wifi/](https://ladvien.com/kali-pi-headless-wifi/)

[https://medium.com/@TheNeelOfficial/headless-kali-linux-in-a-raspberry-pi-9e54c16c2475](https://medium.com/@TheNeelOfficial/headless-kali-linux-in-a-raspberry-pi-9e54c16c2475)

[https://www.notion.so/Kali-Hacking-Kit-7d215e12b05040c9b9a0571c8fe7eb2f#35314b5711094a5e8cbad674ddc01cc2](https://www.notion.so/Kali-Hacking-Kit-7d215e12b05040c9b9a0571c8fe7eb2f)

> simple answer: raspberry pi OS checks for /boot/wpa_supplocant.conf on startup - kali-pi does not - this isn't a raspberry pi feature, it's a Raspberry Pi OS feature - not a fun experience for my first pi - why would you use obscure distro for your first pi? kali is not for newbies, it's for 1337 h4x0r5

Jedyna możliwość headless install kali linux on raspberry pi to ethernet connection.
