# Scanning & Enumeration

kioptrix **john**/**TwoCows2**

## 1. Nmap

```sh
$ IP=<insert IP address>
$ nmap -T4 -p- -vv -A $IP

Starting Nmap 7.91 ...
```

Discovery of ports : 22, 80, 111, 139, 443, 32768  

## 2. Ports review

### 2.1. Port 80 open

```sh
$ nikto -h http://$IP

- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.0.82
```

Discovery of a cve : CVE-2002-0082

### 2.2. Port 139 open

**metasploit**

```sh
$ msfconsole
       =[ metasploit v6.0.52-dev                          ]
+ -- --=[ 2147 exploits - 1143 auxiliary - 365 post       ]
+ -- --=[ 592 payloads - 45 encoders - 10 nops            ]
+ -- --=[ 8 evasion                                       ]

msf6 > search smb_version
XX  auxiliary/scanner/smb/smb_version ...

msf6 > use auxiliary/scanner/smb/smb_version

msf6 auxiliary(scanner/smb/smb_version) > set RHOSTS 192.168.0.82
RHOSTS => 192.168.0.82

msf6 auxiliary(scanner/smb/smb_version) > run
[*] 192.168.0.82:139      - SMB Detected (versions:) (preferred dialect:) (signatures:optional)
[*] 192.168.0.82:139      -   Host could not be identified: Unix (Samba 2.2.1a)
[*] 192.168.0.82:         - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

### 2.3. Port 22 open

```sh
$ ssh 192.168.0.82 -oKexAlgorithms=+diffie-hellman-group1-sha1 -c aes128-cbc
```

No banner.

## 3. Vulnerabilities Research

Search for the findings with the versions and potentially exploits.


## 4. More Port Scanners

### 4.1. Masscan

```sh
$ masscan -p1-65535 192.168.0.82
```

Slower than nmap, but displays the ports when found so no need to wait until the end to start.

### 4.2. Metasploit

```sh
msf6 > use auxiliary/scanner/portscan/syn
msf6 auxiliary(scanner/portscan/syn) > set rhosts 192.168.0.82
msf6 auxiliary(scanner/portscan/syn) > use
```

## 4.3. Nessus

