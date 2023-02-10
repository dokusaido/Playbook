## Mobile Pentest Tools (iOS and Android)
  - [Frida](https://github.com/frida/frida/releases)
  - [Objection](https://github.com/sensepost/objection)
  - [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)
  - [Burp](https://portswigger.net/burp)

```
# Load Frida Server in device && run objeciton
adb push /PATH/FRIDA_SERVER/DOWNLOADED/frida-server /data/local/tmp/.
adb shell "chmod 755 /data/local/tmp/frida-server"
adb shell "/data/local/tmp/frida-server &"
objection --gadget com.vendor.app.xx explore

# Run JS script in Frida
frida -U -f com.vendor.app -l script.js com.vendor.app.version --no-pause

# Run MobSF
docker pull opensecurity/mobile-security-framework-mobsf
docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest

# Redirect mobile traffic to Burp Proxy
Add proxy in Mobile WIFI settings connected to Attacker Host Wifi pointing to 192.168.X.1:8080
Vbox Settings Machine -> Network -> Port Forwarding -> 8080
Burp Proxy -> Options -> Listen all interfaces
```

## Android Specific Tools
  - [Jadx](https://github.com/skylot/jadx) `jadx-gui`
  - [Genymotion](https://www.genymotion.com/download/)
  - [NoxPlayer](https://bignox.com/)
  - [Androbugs](https://github.com/AndroBugs/AndroBugs_Framework) `python androbugs.py -f /root/android.apk`
  - [Androwarn](https://github.com/maaaaz/androwarn)  `pip3 install androwarn && androwarn /root/android.apk -v 3 -r html`

```
docker pull opensecurity/mobile-security-framework-mobsf
docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

- [adb](https://developer.android.com/studio/command-line/adb?hl=es-419)
- [adb-xda](https://forum.xda-developers.com/showthread.php?t=2588979)

```
# In host
C:\Users\$USER\AppData\Local\Android\Sdk\platform-tools\adb devices
# Nox adb in host
"C:\Program Files (x86)\Nox\bin\nox_adb" devices
# In Kali
adb connect IP:PORT/ID - connect by ip/port
adb devices - list devices connected
adb shell - get device shell 
adb push - push file into device
adb install file.apk - install apk

# Untar Android Backup file (*.ab files)
( printf "\x1f\x8b\x08\x00\x00\x00\x00\x00" ; tail -c +25 backup.ab ) |  tar xfvz -
```

- [Xposed Framework](https://repo.xposed.info/module/de.robv.android.xposed.installer)
	- [RootCloak](https://repo.xposed.info/module/com.devadvance.rootcloak2)
	- [SSLUnpinning](https://repo.xposed.info/module/mobi.acpm.sslunpinning)

- [Frida Scripting Guide](https://neo-geo2.gitbook.io/adventures-on-security/frida-scripting-guide/frida-scripting-guide)

## Check for information/files stored in device

```
/data/data/
/data/data/com.app/database/keyvalue.db
/data/data/com.app/database/sqlite
/data/app/
/data/user/0/
/storage/emulated/0/Android/data/
/storage/emulated/0/Android/obb/
```

## Check for some sensible string stored in device (like passwords, users, tokens, JWT...)

```
find /data/app -type f -exec grep --color -Hsiran "FINDTHIS" {} \;
```

## Install Burp Certificate (Android 7+)

```bash
#!/bin/bash

curl -s http://burp/cert -x http://127.0.0.1:8080 -o cacert.der
openssl x509 -inform DER -in cacert.der -out cacert.pem
export CERT_HASH=$(openssl x509 -inform PEM -subject_hash_old -in cacert.pem | head -1)
adb root && adb remount
adb push cacert.pem "/sdcard/${CERT_HASH}.0"
adb shell su -c "mv /sdcard/${CERT_HASH}.0 /system/etc/security/cacerts"
adb shell su -c "chmod 644 /system/etc/security/cacerts/${CERT_HASH}.0"
rm -rf cacert.*
```