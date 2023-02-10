	A simple guide on how to get started with iOS penetration testing.

## Jailbreak Tools
	Information is outdated. Please feel free to help out with a PR.

| JB | Devices | Version |
|----|---------|---------|
| [checkra1n](https://checkra.in/)                           | A7-A11   | latest iOS        |
| [unc0ver](https://unc0ver.dev/)                            | All      | iOS 11.0 - 13.5   |
| [odyssey](https://theodyssey.dev/)                         | All      | iOS 13.0 - 13.7   |
| [fugu](https://github.com/LinusHenze/Fugu)                 | A10-A10X | iOS 13 - 13.5.1   |
| [chimera](https://chimera.coolstar.org/)                   | All      | iOS 12.0 - 12.5   |
| [rootlessJB4](https://github.com/brandonplank/rootlessJB4) | A7-A11   | iOS 12.0 - 12.4.8 |
| [electra](https://coolstar.org/electra/)                   | All      | iOS 11.0 - 11.4.1 |


## Cydia Sources
- Spark - https://sparkdev.me/
- Ivano Bilenchi - https://ib-soft.net/cydia/
- Ryan Petrich - https://rpetri.ch/repo/
- Junes iPhone - https://junesiphone.com/supersecret/
- TigiSoftware - https://data.tigisoftware.com/cydia/
- Bingner - https://apt.bingner.com/
- XenPublic - https://xenpublic.incendo.ws/
- Nepeta - https://repo.nepeta.me/
- Skitty - https://skitty.xyz/repo/
- PoomSmart - https://poomsmart.github.io/repo/
- Packix - https://repo.packix.com/
- Evelyn's Collection - https://evynw.github.io/
- Julio Verne - https://julioverne.github.io/
- BigBoss - http://apt.thebigboss.org/repofiles/cydia/
- Chairz - https://repo.chairz.com/
- Dynastic - https://repo.dynastic.co/
- CreatureCoding - https://creaturecoding.com/repo/
- Buufjuiced - https://buufjuiced.yourepo.com/
- ModMyi - http://apt.modmyi.com/
- ZodTTD & MacCiti - http://cydia.zodttd.com/repo/cydia/

## Intercepting Traffic using Burp Suite
1. Bypass SSL pinning
  - Cydia dependencies
    - Debian Packager
    - Cydia Substrate
    - PreferenceLoader
  - Download latest release of ssl-kill-switch2 
    - https://github.com/nabla-c0d3/ssl-kill-switch2/releases
  - Install

```bash
dpkg -i <package>.deb
killall -HUP SpringBoard
```

  - Install CA certificate
    - Turn on burp proxy
    - Configure Wifi proxy settinngs
    - http://burp
    - Install certificate
  - Mobile Assistant
    - https://portswigger.net/burp/documentation/desktop/tools/mobile-assistant/installing
    - enable Burp proxy on all interfaces
    - add as a source to cydia and install mobile assistant

---

## Tools
  - [Frida](https://frida.re/)
  - [FireCat](https://github.com/BishopFox/firecat)
  - [Cycript](http://www.cycript.org/)
  - [Grapefruit](https://github.com/ChiChou/Grapefruit)
  - [Needle](https://github.com/FSecureLABS/needle)
  - [iRET](https://github.com/S3Jensen/iRET)
  - [Clutch](https://github.com/KJCracks/Clutch)
  - [iDB](https://github.com/dmayer/idb)
  - [BinaryCookieReader](https://github.com/as0ler/BinaryCookieReader)
  - [iSpy](https://github.com/BishopFox/iSpy)
  - [iWep Pro](http://cydia.saurik.com/package/com.iwazowski.iweppro5/)
  - [3UTools](http://www.3u.com/)


## Miscellaneous

- Fix PreferenceLoader for A12 devices that are using Chimera and Sileo
```text
1. Reboot & RootFS 
2. Reboot & RootFS
3. Reboot & Jailbreak
4. Install Cephei (+ dependencies)
5. Add rpetri.ch/repo
6. Update RocketBootstrap
```

- Directories to check for tweak remains
```
/var/mobile/Library/Caches
/var/mobile/Library/Preferences
/var/root/Library/Caches
/var/root/Library/Preferences
```

- Check for information/files stored in device (3U TOOLS - SSH Tunnel):

```
/private/var/mobile/Containers/Data/Application/{HASH}/{BundleID-3uTools-getBundelID}
/private/var/containers/Bundle/Application/{HASH}/IPA_NAME}
/var/containers/Bundle/Application/{HASH}
/var/mobile/Containers/Data/Application/{HASH}
```

- Fast finds to check sensible strings stored in devices:

```
find /data/app -type f -exec grep --color -Hsiran "FINDTHIS" {} \;
find /data/app -type f -exec grep --color -Hsiran "\"value\":\"" {} \;

# Manual review
find APPPATH -iname "*localstorage-wal" 
```