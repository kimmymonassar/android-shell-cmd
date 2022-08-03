# android-shell-cmd


## adb
adb shell  
adb cmd package list-packages  
adb shell am start -n com.termux/.HomeActivity <-- any apk  
adb shell input text <text> <-- encode spaces to %s  
adb shell input keyevent ENTER  


## termux
logcat -s "sshd:*" <-- any  
pkg install tsu <-- tsu = su, also contains sudo  
wget -O - https://raw.githubusercontent.com/its-pointless/its-pointless.github.io/master/setup-pointless-repo.sh | sh  
