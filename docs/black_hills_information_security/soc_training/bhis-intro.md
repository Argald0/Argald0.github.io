# SOC Core Skills Training

## 1 Summary

What are we going to cover ?

- Intro to Windows
- Intro to Linux
- Intro to TCP/IP
- Basics & fundamentals
- Core things to learn to work at the BHIS SOC
- This class is meant to feed into the Intro to Security class

#### What to do on a bad day ?

You need a plan !  
**Plans are useless, planning is indispensible**  
Don't panic !

## 2 Let's start with Windows

First things to do **network connections**:
- netstat
- netview
- net use
- net session

*run cmd as admin*

### 2.1 Network Connections 

#### 2.1.1 C:\\> net view

- allows to look at shares
- attackers like to set shares as staging areas inside of a network
- pull files to one location and then exfil out
- what is normal ?


If you're a SOC analyst and if there is a net command firing, it's an attacker trying to mount shares

#### 2.1.2 C:\\> net session

- who is currently talking to the current system ?
- need to see this as a chain

#### 2.1.3 C:\\> net use

- who is the system talking to ?
- opposite of net session

#### 2.1.4 C:\\> netstat

- lots of flags
- shows network connections

##### 2.1.4.1 C:\\> netstat -naob

Shows all TCP and UDP connections :
- **-a** : all ports
- **-n** : what port ?
- **-o** : what Process ID ?
- **-b** : what exe ?

**PID 4 = system process**

##### 2.1.4.2 C:\\> netstat -f

fully qualified name

### 2.2 Windows Processes

After checking the network connections we need to check the processes

#### 2.2.1 C:\\> takslist /svc

Allows to check if the svchosts are legit 

#### 2.2.2 C:\\> tasklist /m

Dumps all DLLs used by each process  
- tasklist /m \<dll name\> : to check what uses that one dll
- tasklist /m /fi "pid eq \<process id>"


## Dr Cole's 3 metrics 

top 10 with, 1. most # of connections, 2. longest duration connections, 3. largest size connections.


**PlumHound & PingCastle**