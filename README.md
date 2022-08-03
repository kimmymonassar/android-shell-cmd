# android-shell-cmd

## adb
adb shell  
adb cmd package list-packages  
adb shell am start -n com.termux/.HomeActivity - any apk  
adb shell input text <text> - encode spaces to %s  
adb shell input keyevent ENTER  

## termux / shell
whoami  
pwd  
logcat -s "sshd:*" - any  
tsu - termux su variant, tsu package also adds sudo  
wget -O - https://raw.githubusercontent.com/its-pointless/its-pointless.github.io/master/setup-pointless-repo.sh | sh  
file <file> - show file info  
find /etc -type f -iname file1.txt - find file in folder /etc, f = file, d = directory. (wildcard available for filenames)  

### termux ssh server setup
pkg install openssh  
passwd - set password  
ifconfig - look for inet ip adress  
sshd - add **d** param for debug logging  

connect with ssh <username>@<ipadress> -p8022 (linux, use putty/wsl for windows)  
  
**to be able to log in as root edit $PREFIX/etc/ssh/sshd_config and add "PermitRootLogin yes", use same password as set with passwd command**

## termux packages
tsu  
neofetch  
wget  
vim  
openssh  
gcc (needs its-pointless repo)  
metasploit (needs pkg install unstable-repo)  
docker (and docker-compose)  
