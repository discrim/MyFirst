# Linux Bash Cheatsheet
Also about WSL (Windows Subsystem for Linux)
1. [WSL 실제 경로 / Actual directory of WSL](#wsl-실제-경로--actual-directory-of-wsl)
1. [Reset the Password in WSL](#reset-the-password-in-wsl)
1. [Global Environment Variable](#global-environment-variable)
1. [How to install Ananconda on Linux](#how-to-install-anaconda-on-linux)
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
### Global Environment Variable
Ref: [Blog](https://memory.today/dev/23)
1. Backup `/etc/profile` with `sudo`.
	```
	$ sudo cp /etc/profile /etc/profile_bak
	```
1. Open `/etc/profile` with `sudo`.
	```
	$ sudo vim /edit/profile
	```
1. Go to the last line (in `vim`, use `Shift + G` in `command mode`).
1. Use `export` to set variable and directory (or full path including filename), and save and exit.
	```
	export MYVAR=~/my_project/my_folder
	export YOURVAR=~/my_project/my_folder/my_executable
	```
1. Run `source` to reflect the change, or simply restart.
	```
	source /etc/profile
	```
1. With prefix `$`, the variables are callable at any place.
	```
	$ cd $MYVAR
	$ $my_executable
	```
1. If it is not working, use `echo` to check if the change is applied.
	```
	$ echo $MYVAR
	/home/(username)/my_project/my_folder
	$ echo $YOURVAR
	/home/(username)/my_project/my_folder/my_executable
	```
### How to install Anaconda on Linux
```bash
# Go to a directory to install Anaconda. I prefer /home
cd /home
cd # Equivalent

# Download Anaconda
wget https://repo.anaconda.com/archive/Anaconda3-2020.11-Linux-x86_64.sh

# Install Anaconda
bash Anaconda3-2020.11-Linux-x86_64.sh

# Let the Linux know that we just installed Anaconda
source ~/.bashrc

# Done! Now continue as using Anaconda on Windows
conda create -n my-env python=3.7.10
conda activate my-env
conda list
conda install -c pytorch pytorch
...
```
The release of anaconda (`2020.11` part of the code block above) may have to be changed as newer anaconda is out.
