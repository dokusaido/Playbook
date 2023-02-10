## Change MAC Address

- View interfaces

```
iwconfig
```

- Disable card

```
ifconfig wlan0 down
```

- Get a new random MAC address

```
macchanger --random wlan0
```

- Enable card

```
ifconfig wlan0 up
```