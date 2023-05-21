run command : **sudo nmap -sC -sV -T4 -sS  -vv 192.168.1.8
**

Result : 

<img width="952" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/09f34bbd-70c0-45c5-ae76-728fd7db20a8">
<img width="863" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/6db26bbf-1ff5-4e77-acc1-39048ac02536">



run command : **smbclient -L //192.168.1.8/ -N**

<img width="489" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/94a580fd-ee1f-4b5b-b3cc-22b345af06dc">


Login with smbclinet : **smbclient \\\\192.168.1.8\\anonymous

<img width="469" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/b7d0a191-9a7c-4898-92de-866840ff909f">

download attention.txt with command : **get attention.txt**

<img width="465" alt="image" src="https://github.com/psfauzi/Vulnhub_Like_OSCP/assets/49013900/af55aa88-df91-40a1-89e9-e71e96c6842f">
