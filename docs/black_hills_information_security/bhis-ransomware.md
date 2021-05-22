# Emergency Webcast : Ransomware!

## 1. Recent attacks

[Colonial pipeline attack](<https://www.zdnet.com/article/colonial-pipeline-ransomware-attack-everything-you-need-to-know/>) : DarkSide was able to target a pipeline that transports over 100 gallons of fuel daily.  

## 2. Deception

Deception is ***ESSENTIAL*** !  

Attackers are still getting through the high-end EDR products, or just password spraying in order to gain access to the environment... 

We spend so much time trying to secure the endpoint that we started to ignore that companies are still getting compromised. Those security products are all going to fail, then what ?

We need to be looking at the **attack pathways** post-exploitation : password spraying ? kerberoasting ? etc... Attackers use the **usual RedTeam methods** !

## 3. Three types of ransomware


### 3.1. Encrypt OS

One of the first types that come to mind when we think about ransomware is the kind that encrypts the whole Operating System

### 3.2. Encrypt Files
       
The other super famous kind is the one encrypting the files, not the whole workstation.

### 3.3. Blackmail stolen data
        
Last but not least, the kind where the company was stolen important files (potentially life or death situations), and the bad guys are blackmailing the company in order not to release the information.

## 4. Detection/Prevention tools

=== "CanaryTokens"

    Amazing tool to notice an attacker on your network. When you trigger the honeydoc, it can send you an alert, give you the IP address, even get the name of the machine, the credentials of the account connected on it, realize a traceroute, get the exact position of the attacker...

    - It can be put on :
        - shares
        - compromised systems
        - websites (Robots.txt)
        - Email to spammers!
    - When an attacker pops a box, they try to pivot in order to gather more information, trying to find information in doc files... let them find your password.docx ! :wink:

    !!! information ""
        <https://github.com/thinkst/canarytokens>

=== "Honeyaccount"

    - Make sure to **login** to the account at least once
    - Disable the logon hours (in order to make it **effectively disabled**)
    - Put an easy but **really long password**, last changed *long ago*
    - Add a rule to trigger an alert as soon as someone tries to use this account !

=== "RITA"

    BHIS' tool RITA : it can detect Command and Control in an hour !  

    !!! information ""
        <https://www.activecountermeasures.com/free-tools/rita/>

=== "CredDefense toolkit"

    The tool can create kerberoasting cyber detection, because every attacker will try to pivot and escalate by doing kerberoasting.  

    !!! information ""
        <https://github.com/CredDefense/CredDefense>

=== "Raccine"

    Raccine can detect when an attacker tries to delete the windows shadow copies. It intercepts the request and kills the invoking process.

    triggers with :
    ```
    vssadmin.exe...
    vssadmin.exe delete shadows /all /quiet

    or

    wmic.exe...
    
    ```
    

    !!! information ""
        <https://github.com/Neo23x0/Raccine>

=== "Ransomware protection in Windows Security"

    Windows has an integrated tool to prevent ransomware attacks. 


## 5. Ransomware procedure

"According to IBM X-Force, the malware, once deployed, steals data, encrypts systems using Salsa20 and RSA-1024 encryption protocols, and executes an encoded PowerShell command to delete volume shadow copies."

Hence [Raccine](#4-detectionprevention-tools)

*[EDR]: Endpoint Detection & Protection