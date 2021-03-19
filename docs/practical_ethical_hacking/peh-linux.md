# Introduction to Linux

## 1. Navigating the File System

- `$ pwd` : Present working directory.  
- `$ cd /path/to/file` : Change directory.  
- `$ ls -la` : List everything in the folder, even hidden files  
- `$ mkdir /path/to/file` : Make directory.  
- `$ rmdir /path/to/file` : Remove directory.  
- `$ cp /path/to/source /path/to/destination` : Copy file.  
- `$ rm /path/to/file` : Remove file.  
- `$ mv /path/to/source /path/to/destination` : Move file or rename it.   
- `$ locate <filename>` : Locate a file.  
\\--> Use `$ updatedb` to refresh the database.
- `$ echo "something"` : Displays "something".  
- `$ <command> > /path/to/file` : Writes the output of the command in the file.  
```sh
    $ echo "Hello World!" > test.txt
    # Creates a file test.txt in the current directory with "Hello World!" written inside.
```
- `$ man <command>` : Manual page for that command.  
  

## 2. Users and Privileges

When doing a `ls -la` we can see the file details.

```sh
$ ls -la
total 148
drwxr-xr-x 14 kali    kali     4096 Mar  3 17:16 .
drwxr-xr-x  3 root    root     4096 Jul 27  2020 ..
-rwxr--r--  1 walbert support     0 Oct 31 11:06 test
```
![linux-file-permissions](images/linux-file-permissions.png)

- `$ cat /etc/passwd` to see users.
- `$ passwd` : Change password of the current user.  
- `$ cat /path/to/file` : Displays the file in terminal.  
- `$ chmod 777 /path/to/file` : Change mode (rwx) of the file.  
- `$ adduser <username>` : Add a user "username".  
- `$ su <user>` : Switch user.  
- `$ sudo <command>` : Super User DO command.

Sudoers file: anyone in there can use the `sudo` command.

## 3. Network Commands

- `$ ifconfig` : Shows the different network information. 
- `$ iwconfig` : Wireless network information.  
- `$ ping <ip>` : Sends ICMP packet (ping) to the given ip.  
- `$ arp -a` : Shows the IP addresses talking to you and the MAC addresses associated.
- `$ netstat -ano` : Shows active connection on your machine (interesting during pentest to see if the machine is talking to another one).  
- `$ route` : Prints the routing table.

These are becoming deprecated, now the `ip` command is the goto :

- `$ ip a` : IP address, Network, Broadcast
- `$ ip n` : ARP table
- `$ ip r` : Routing table

## 4. Installing and Updating tools

```sh
$ apt update && apt upgrade
# Updates the system
```

#### 4.1. Install package

```sh 
$ apt install pip
# Installs pip
```

#### 4.2. From Github

```sh
$ cd /opt
# Downloads in the opt file : good practice

$ git clone https://github.com/username/repository.git
# Clones the repository on the local machine
```

#### 4.3. Install gedit

```sh
$ sudo apt install gedit

$ gedit test.txt
```

## 5. Viewing, Creating and Editing Files

```sh
$ echo "test" > test.txt
# Overwrites a test.txt file with "test" inside

$ cat test.txt
test

$ echo "test2" >> test.txt
# Appends the echo standard output to the file test.txt

$ cat test.txt
test
test2
```

- `$ touch /path/to/file` : Creates an empty file with the mentioned name.

## 6. Scripting with Bash

Let's make a script to grab the IP address after a successful ping

#### 6.1. Command to extract only the IP after the ping

```sh
$ ping 192.168.4.29 -c 1 > ip.txt

$ cat ip.txt
PING 192.168.4.29 (192.168.4.29) 56(84) bytes of data.
64 bytes from 192.168.4.29: icmp_seq=1 ttl=64 time=0.028 ms
--- 192.168.4.29 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.026/0.027/0.029/0.001 ms

$ cat ip.txt | grep "64 bytes"
64 bytes from 192.168.4.29: icmp_seq=1 ttl=64 time=0.028 ms

$ cat ip.txt | grep "64 bytes" | cut -d " " -f 4
192.168.4.29:

$ cat ip.txt | grep "64 bytes" | cut -d " " -f 4 | tr -d ":"
192.168.4.29
```

#### 6.2. The Script

```sh
$ vim ipsweep.sh
# Creates the file sweep.sh and opens vim editor
```

The script should look like this :

```sh
#!/bin/bash

if [ "$1" == "" ]
then
echo "You forgot an IP address!"
echo "Syntax : ./ipsweep.sh 192.168.1"

else
for ip in `seq 1 254`; do
ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
done
fi
# When running the script, we also give the beginning of the IP address : $1
# "&" Allows to run multiple commands at the same time
```

[ipsweep.sh](files/ipsweep.sh)

```sh
$ chmod +x ./ipsweep.sh
# Allows us to execute the script

$ ./ipsweep.sh 192.168.1
192.168.1.1
192.168.1.22
192.168.1.23
192.168.1.24
192.168.1.53
```

We can then put all of these IP addresses in a file, in order to help our scanning through nmap : 

```sh
$ ./ipsweep.sh 192.168.1 > valid_ipaddress.txt

$ for ip in $(cat valid_ipaddress.txt); do nmap $ip; done
```