# Android shell/Termux cheat sheet

## adb
`adb help` - List all commands  
`adb shell` - Connect to android shell  
`adb shell cmd package list packages` - List all packages   
`adb shell cmd package list packages -f **name**` - Show specific package and associated file(s)  
`adb shell input text "text"` - Encode spaces to %s  
`adb shell input keyevent ENTER`  - Send keyevent, also able to send touch events  
`adb push C:\Windows\System32\config /sdcard/` - Transfer file from client to host  
`adb pull /sdcard/video.mp4 C:\Windows\System32\config` - Transfer file from host to client  

## termux / shell
`pkg update && pkg upgrade -y`  - Update and upgrade packages, `y` param for auto confirmation  
`pkg autoclean` - Remove outdated packages  
`whoami` - Show current user  
`pwd` - Print working directory  
`chmod +x ./foo.sh` - Make file executable  
`logcat -s "sshd:*"` - Print logcat for `sshd` process, works for all processes that log to logcat  
`tsu` - Termux `su` variant, needs tsu package installed. Also enables `sudo` command  
`wget -O - https://raw.githubusercontent.com/its-pointless/its-pointless.github.io/master/setup-pointless-repo.sh | sh` - Download and run remote file, can be used for other filetypes than `.sh`.  
`file ./foo.c` - Show file info, `--help` for more options  
`find /etc -type f -iname file1.txt` - Find file in folder /etc, f = file, d = directory. Wildcard can be applied to both name and extention, for example `*.txt` to find all text files in /etc.  
`tar cvf - foldername | lz4 - foldername.tar.lz4` - Bundle a folder to a .tar file and then compress it with lz4. Note: if lz4 command is not recognized then call it with the full path. Easiest way to get the path is by using the `find` command.  

### termux ssh server setup
`pkg install openssh`  
`passwd` - Set user password  
`ifconfig` - look for inet ip adress  
`sshd` - add `d` param for debug logging  

Connect with `ssh username@ipadress -p8022` (Linux/Mac, use Putty or WSL for Windows) Default port is 8022  
To be able to log in as root edit `$PREFIX/etc/ssh/sshd_config` and add `PermitRootLogin yes`, use same password as set with `passwd` command  

### rclone
`rclone ls remote:` - list files in root directory of remote drive called `remote`  
`rclone mount remote:/ rclone/ --daemon --allow-root` - mount remote: drive as a VFS, the second argument specifies the full path to an empty folder on the local filesystem that can be used as an entry point   
`rclone move source:path dest:path` - move files from source to dest, use `--progress` flag to show real time statistics`  
`rclone moveto source:path dest:path` - move single files from source to dest, also has support for progress flag  

View [rclone docs](https://rclone.org/commands) for more useful commands    

## termux packages
* tsu  
* neofetch  
* wget  
* vim  
* openssh  
* gcc - See install instructions below  
* metasploit - Needs pkg install unstable-repo  
* docker - docker-compose also available  
* git  
* lz4  
* rclone
* ...

# gcc compiler
### Add its-pointless repo to Termux
`echo "deb https://its-pointless.github.io/files/24 termux extras" > $PREFIX/etc/apt/sources.list.d/pointless.list` - For android 5 & 6 use 21 instead of 24  
`apt-get install gnupg` - If not already installed  
`curl -fsSL https://its-pointless.github.io/pointless.gpg | sudo apt-key --keyring /etc/apt/trusted.gpg.d/pointless.gpg add` - Add gpg key as trusted  
`apt-get update`  

### Install gcc and switch from clang  
`apt-get install gcc-11`  
`setupgcc-11` - To switch back to using clang run `setupclang`  
`setup-patchforgcc`  

## gcc usage
1. Create "Hello World" boilerplate: `printf "#include <stdio.h>\n\nint main (void)\n{\n  printf(\"Hello World\");\n  return 0;\n}" > foo.c`  
2. Write your code: `vim foo.c`  
3. Compile with gcc: `gcc foo.c -o output -D__BIONIC_VERSIONER`  
4. Run the compiled output file: `./foo`  

