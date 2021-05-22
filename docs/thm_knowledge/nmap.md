# Nmap
<div style="text-align: right"> <sub>from the TryHackMe room of the same name</sub> </div>

Network Mapper (Nmap) : port scanner.

### First Full Scan :

```sh
export IP=<IP>
nmap -A -T4 -p- $IP -vv > "$IP-full_scan.txt"
```

## 1 Nmap switches

**Switch**|**Flag**
:-:|:-:
**S**yn **s**can|`-sS`  
**U**DP **s**can|`-sU`
**O**perating System discovery|`-O`
**V**ersion of **s**ervices|`-sV`
Increase **v**erbosity|`-v`
Increase **v**erbosity lvl **2**|`-vv`
Output in 3 major formats|`-oA`
**N**ormal format **o**utput|`-oN`
**G**repable format **o**utput|`-oG`
**A**ggressive mode (service, OS, traceroute & common script scanning)|`-A`
**T**iming template 5|`-T5`
Scan **p**ort 80 and from 443 to 500|`-p 80, 443-500`
Scan *ALL* **p**orts|`-p-`
Activate **script**|`--script`
Activate all **script**s in the **vuln** category|`--script=vuln`
