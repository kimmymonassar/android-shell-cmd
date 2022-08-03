# android-shell-cmd

## adb
adb shell  
adb cmd package list-packages  
adb shell am start -n com.termux/.HomeActivity - launch any apk  
adb shell input text "text" - encode spaces to %s  
adb shell input keyevent ENTER  

## termux / shell
pkg update && pkg upgrade -y  
pkg autoclean  
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
git  

## gcc compiler
### add its-pointless repo  
echo "deb https://its-pointless.github.io/files/24 termux extras" > $PREFIX/etc/apt/sources.list.d/pointless.list - (for android 5 & 6 use 21 instead of 24)  
apt-get install gnupg  
curl -fsSL https://its-pointless.github.io/pointless.gpg | sudo apt-key --keyring /etc/apt/trusted.gpg.d/pointless.gpg add  
apt-get update  
### install gcc and switch from clang  
apt-get install gcc-11  
setupgcc-11 (to switch back to using clang run setupclang)  
setup-patchforgcc  

### gcc usage
**printf "#include <stdio.h>\n\nint main (void)\n{\n  printf(\"Hello World\");\n  return 0;\n}" > hello.c**  
use vim/nano to write ur code: **vim hello.c**  
**gcc hello.c -o output -D__BIONIC_VERSIONER**  
finally run the compiled output file: **./hello**  
