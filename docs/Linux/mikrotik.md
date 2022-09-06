# Mikrotik

<https://www.youtube.com/watch?v=1ZJ-pM89N7o>

Wireguard is the future - if you ain’t running Router OS7 RC beta then you a SISS

The most secure VPN is Mullvad

Networks:

Starlink SMART - for smart home devices

- open VPN
- raspberry pi zero bramka (dostęp po ssh)
- xiaomi czajnik
- xiaomi odkurzacz
- pralka LG
- suszarka LG
- bramka IKEA
- apple tv

Starlink HOME - General network

- open VPN
- raspberry pi 3 (dostęp po ssh)
  - serwer drukarki
  - serwer docker
- computer PC
- macbooks
- phones
- serwer NAS

Starlink GUEST - network for guests

- rest of devices

## Usefull commands

```sh
ip address print

# BACKUP IMPORT
system backup load name=backup05052008.backup

# BACKUP EXPORT
system backup save name=backup05052008

# RESET CONFIG
system reset-configuration
```

<https://www.youtube.com/channel/UC3JS09xpXbXaHyRuVZondvQ>
<https://www.youtube.com/c/TheNetworkBerg>

## How to configure OPEN VPN

[Sprawdzony poradnik!](https://nsix.pl/kb/serwer-openvpn-na-mikrotik-chr/)

[Sprawdzony poradnik 2!](https://grzegorzkowalik.com/mikrotik-openvpn-server/)

https://gist.github.com/SmartFinn/8324a55a2020c56b267b#add-a-new-user
https://mum.mikrotik.com/presentations/ID16/presentation_3277_1476686469.pdf

In case with not searchable local devices you should:

> Please don't forget on lan interfaces to set them up as proxy-arp.
