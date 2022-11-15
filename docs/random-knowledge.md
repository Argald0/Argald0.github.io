# Random knowledge

## Virtualization

### Virtualbox

#### Fullscreen

On guest machine:

```sh
$ sudo apt-get update
$ sudo apt-get install -y virtualbox-guest-utils virtualbox-guest-x11
$ reboot
```

#### Fullscreen Debian 11 Bullseye

On Virtualbox:

**Devices** > **Insert Guest Additions CD image**

On Guest:

```sh
$ sudo mount /dev/cdrom /mnt
$ ls -1 /mnt
AUTORUN.INF
autorun.sh
cert
NT3x
OS2
runasroot.sh
TRANS.TBL
VBoxDarwinAdditions.pkg
VBoxDarwinAdditionsUninstall.tool
VBoxLinuxAdditions.run
VBoxSolarisAdditions.pkg
VBoxWindowsAdditions-amd64.exe
VBoxWindowsAdditions.exe
VBoxWindowsAdditions-x86.exe
$ sudo apt update -y && sudo apt upgrade
$ sudo apt install dkms linux-headers-$(uname -r) build-essential  #Required packages
$ sudo sh /mnt/VBoxLinuxAdditions.run
$ systemctl reboot -i
```
To uninstall the guest additions run : `sudo sh /mnt/VBoxLinuxAdditions.run uninstall`

## Useful aliases and functions

*For zsh, add `source $HOME/.aliases` in the `.zshrc` file`

```sh
# create a folder and immediately get in:
mkcd () {
    mkdir -p -- "$1" && cd -P -- "$1"
}
seurch () {
    cat ~/.bash_history | grep "$1"
}
alias ..='cd ../'
alias ...='cd ../../'
alias ....='cd ../../../'
alias .....='cd ../../../../'
alias ip='ip --color'
```

## Disks details on Linux

### Disk information

`lsblk -l`

[source](<https://www.cyberciti.biz/faq/find-hard-disk-hardware-specs-on-linux/>)

## Manual package installation

### Debian

```sh
sudo dpkg -i package_name.deb
```

## Add user to sudoers

```sh
usermod -aG sudo username
```


udp scan : sudo nmap -sU -sV - 10.10.11.124 --min-rate 7500 -F