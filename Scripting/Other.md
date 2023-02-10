## Read file contents
```bash
cat *
cat file.txt
more file.txt
head file.txt
tail file.txt
echo < file.txt
grep . file.txt
while read line; do echo $line; done < file.txt
```

## Bash port scanner
> John Hammond
```bash
curl http://10.10.10.1:[30000-60000]
```

## Find SUID files
```bash
find "$DIRECTORY" -perm /4000     # SUID
find "$DIRECTORY" -perm /u=s      # SUID
find "$DIRECTORY" -perm /2000     # SGID
find "$DIRECTORY" -perm /g=s      # SGID
find "$DIRECTORY" -perm /6000     # SGID + SUID
find "$DIRECTORY" -perm /u=s,g=s  # SGID + SUID
```

## Execute command without keeping it in history
```bash
<your_secret_command>; history -d $((HISTCMD-1))
<your_secret_command>; history -d $(history 1)
```