# Linux Bash Cheatsheet
Also about WSL (Windows Subsystem for Linux)
1. [WSL 실제 경로 / Actual directory of WSL](#wsl-실제-경로--actual-directory-of-wsl)
1. [Reset the Password in WSL](#reset-the-password-in-wsl)
### WSL 실제 경로 / Actual directory of WSL
- Source: [Windows 10 - Ubuntu on Windows 10 서로간 파일 시스템 접근하기](https://snowdeer.github.io/windows/2018/01/07/windows10-ubuntu-file-directory/)  
`C:\Users\<username>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\rootfs`
### Reset the Password in WSL
Source: [StackExchange](https://askubuntu.com/questions/772050/reset-the-password-in-ubuntu-linux-bash-in-windows)
1. Open `bash` and make a note of your Linux username.
```
$ whoami
```
1. Open Windows Command Prompt with admin rights and change the default user of Linux to root.
```
>ubuntu config --default-user root
```
If using Ubuntu 18.04, then
```
>ubuntu1804 config --default-user root
```
1. Open `bash` and use `passwd` command with your user name from the first step to change the user's password.
```
$ passwd your_username
```
1. Open Windows Command Prompt with admin rights and change the default user of Linux back to the normal user.
```
>ubuntu config --default-user your_username
```
If using Ubuntu 18.04, then
```
>ubuntu1804 config --default-user your_username
```
