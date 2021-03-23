# Nmap

Network Mapper (Nmap) : port scanner.

### Frequently Used Commands :

```sh
export IP=<IP>
nmap -A -T4 -p- $IP -vv > $IP-full_scan.txt
```