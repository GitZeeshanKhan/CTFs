First of all I downloaded the Jangow01 machine you can get it by this link: https://www.vulnhub.com/entry/jangow-101,754/ after downloading import in virtual box. Then I turn on Kali Linux machine. And ping the jangow01 machine from kali Linux. After that I scanned the jangow machine though its IP from Nmap in kali Linux. Here is the screenshot below.

![image](https://github.com/user-attachments/assets/5b6eac67-b319-4656-9aa6-c336d91179a1)
<h3 align=center>
nmap –sV target_IP
</h3>

After running this command I came t o know that port 21 means ftp is open. But to connect with it. The username and password of jangow machine is required. So I took a deep dive. Enter the jangow IP Address in the browser of kali linux. Hence these both system are on the same network. So when I entered I got the descent web page and it can be seen in below screenshot. I clicked different menu but when clicked Buscar (French words means To Search) so I got blank page.

![pic1](https://github.com/user-attachments/assets/15d3b318-d969-4334-ac11-003dc9ed776a)

I started to get any vulnerability entered ls with the url but didn’t get any useful result. But when I added ls –all so got hint.
<div align=center>

![pic2](https://github.com/user-attachments/assets/8e9243c6-376a-4b95-9254-362e9f51593c)
![pic3](https://github.com/user-attachments/assets/1035223c-adc0-496f-b092-c70a4939c3cc)

</div>

I clicked that left mouse button and click the view page source to get the result in better way. And to find further hints.

![image](https://github.com/user-attachments/assets/8120c27e-494b-4469-b7f4-b9e93478afca)
 
I typed pwd to check the current working directory. I got the current directory.

![image](https://github.com/user-attachments/assets/016e6e97-7915-4429-a586-ffc9d80d80d8)

<h3 align=center>cat /var/www/html/.backup</h3>

By this got the data inside backup file. That’s how I got username and password to get access of general user in the jangow machine.
 
![image](https://github.com/user-attachments/assets/c3dccaea-c204-4fc9-841e-4bef2bdd934d)


I opened the terminal in kali linux and type ftp and jangow machine ip then entered same username and password got from backup file.
<h2 align=center>
Usernmae : jangow01 
|||
Passoword : abygurl69
</h2>

![image](https://github.com/user-attachments/assets/f7326c86-ca4c-4cb3-8e3e-a0dd6e49bcb8)


I entered cd html and then entered ls –all to get all hidden files in the directory. Then I tried to upload file but got error. After finding solution I opened ftp server in that directory in which file I wanted to put here.
 
![image](https://github.com/user-attachments/assets/b48b27f8-3bf8-4002-96eb-9ceb683ad35c)
 
When I entered ls –all so I got many files as a result I typed get user.text because this file seems to be given any hint.

![image](https://github.com/user-attachments/assets/3d80a7bd-779b-4fd2-92ce-0bf2dc79639a)

But when I opened I got find any relevant output. Then I skip and went forward. It’s time to get the root account because in this account capture is not found. I typed unmae –a in the jangow machine. And get jangow machine version.
 
I starting finding any exploit which can be exploited to get the Privilege Escalation and can get the access of root account from any backdoor. When I typed linux 4.4.0-31-generic exploit in the google. So I got exploit to achieve this g oal.

![image](https://github.com/user-attachments/assets/6e445269-b869-4377-b66e-4fe13e4b48ff)


I downloaded this exploit and put in ftp server from the kali linux. Give it
executable permission by typing chmod +x file_name.c then I executed exploit.

![image](https://github.com/user-attachments/assets/b9ded331-0657-4e1e-9bf3-63e88726bad4)
 
After that type whoami so root was showing. It means I got root account. It’s time to capture the flag.

I typed cd root and then entered ls to check how many files are there. Finally I typed cat proof.txt That’s How I crack this machine and capture the flag.
