# Hydra
<div style="text-align: right"> <sub>from the TryHackMe room of the same name</sub> </div>

## Typical commands

=== "SSH"

    ```sh
    $ hydra -l <username> -P <full path to pass> 10.10.34.43 -t 4 ssh
    ```

=== "Web Form"

    ```sh
    $ hydra -l <username> -P <wordlist> 10.10.34.43 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
    ```

## Introduction

Hydra is a brute force online password cracking program; a quick system login password 'hacking' tool.

Hydra has the ability to bruteforce the following protocols:

-|-|-|-|-
:-:|:-:|:-:|:-:|:-:
Asterisk | AFP | Cisco AAA | Cisco auth | Cisco enable
CVS | Firebird | FTP |  HTTP-FORM-GET | HTTP-FORM-POST
HTTP-GET | HTTP-HEAD | HTTP-POST | HTTP-PROXY | HTTPS-FORM-GET
HTTPS-FORM-POST | HTTPS-GET | HTTPS-HEAD | HTTPS-POST | HTTP-Proxy
ICQ | IMAP | IRC | LDAP | MS-SQL
MYSQL | NCP | NNTP | Oracle Listener | Oracle SID
Oracle | PC-Anywhere | PCNFS | POP3 | POSTGRES
RDP | Rexec | Rlogin | Rsh | RTSP
SAP/R3 | SIP | SMB | SMTP | SMTP Enum
SNMP v1+v2+v3 | SOCKS5 | SSH (v1 and v2) | SSHKEY | Subversion
Teamspeak (TS2) | Telnet | VMware-Auth | VNC | XMPP

## The switches

The different switches : 

Switch|Description
:-:|:-:
`-l <username>`|In order to give a fixed username value to use
`-L <path/to/username/list.txt>`|In order to brute force the username
`-p <password>`|In order to give a fixed password value to use
`-P <path/to/password/list.txt>`|In order to brute force the password
`-t`|Specify the number of threads
