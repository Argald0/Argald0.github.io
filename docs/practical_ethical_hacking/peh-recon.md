# Information Gathering (Reconnaissance)

## 1. Passive reconnaissance overview

Quick review of Physical / Social :

  - Location Information : 
    - Satellite images
    - Drone recon
    - Building layout (badge readers, break areas, security, fencing)
  - Job Information : 
    - Employees (name, job title, phone number, manager, etc...)
    - Pictures (badgephotos, desk photos...)

Web/Host

1. Target Validation : WHOIS, nslookup, dnsrecon
2. Finding Subdomains : Google Fu, dig, Nmap, Sublist3r, Bluto, crt.sh, etc...
3. Fingerprinting : Nmap, Wappalyzer, WhatWeb, BuiltWith, Netcat
4. Data Breaches : HIBP, Breach-Parse, WeLeakInfo

### 1.1. Email address gathering with Hunter.io

**Hunter.io** : Search for email addresses, and compare through LinkedIn

### 1.2. gathering breached credentials with breach-parse

1. **breach-parse** : <https://github.com/hmaverickadams/breach-parse>

Install breach-parse and run as the following example :

```sh
$ cd /opt/Breach-Parse
$ ./breach-parse.sh @tesla.com tesla.txt

Extracting usernames...
Extracting passwords...
```

2. **theharvester** : <https://github.com/laramies/theHarvester> (default kali integrated)

Some ressources require API keys (as Hunter.io)

flag|description
:-:|:-:
`-d`|domain
`-l`|lines; number of results
`-b`|what to search on

```sh
$ theharvester -d tesla.com -l 500 -b google
```

### 1.3. Hunting subdomains

- **sublist3r** :
  - install `sudo apt install sublist3r`
  - run `sublist3r -d tesla.com`
- **crt.sh** :
  - search engine `%.tesla.com` (certificate fingerprinting)
- **Amass** :
  - ([github](<https://github.com/OWASP/Amass>))

For each result, use **Tomnomnom's httprobe** tool to see if the site is alive. [(github)](<https://github.com/tomnomnom/httprobe>)

### 1.4. Identifying website technologies

- **BuiltWith.com** 
- **wappalyzer** : add to firefox, browse the site and use the extension.
- **whatweb** : `$ whatweb https://tesla.com`

### 1.5. BurpSuite

Install process :

- install and run
- setup foxyproxy
- surf the web and let the magic happen :slight-smile:

### 1.6. Google Fu

```txt
site:tesla.com -www filetype:csv
```

Google Fu learning : [site](<https://www.backupassist.com/blog/improving-your-google-fu-how-to-find-anything-you-want>)

### 1.7. Social Media

LinkedIn to get people working for the site, hunter.io to get the email address format --> list of used email addresses.