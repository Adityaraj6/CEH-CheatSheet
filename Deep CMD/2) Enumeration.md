Tools Used
1) gni_setup.exe = scan the entire network from 10.10.10.1 to 10.10.10.25
2) ipscan25.exe = same as gni_setup.exe
3) Netbios Enumerator = enumerate everything like registry shares 
4) nmap GUI = nmap -O IP
5) nbstat -A IP list all the shares 
6) AD_explorer.exe which users has admin privs etc
7) enum4linux -u username -p pass  -P IP 
8) enum4linux -u username -p pass  -S  IP this will list all the shares 
9) on kali
	1) **nmap -sP 10.10.10.0/24** this will scan all the devices present on the given network
	2) nmap -sS IP stealthy scan
	3) msfconsole first snmp_login , snmp_enum 




https://www.youtube.com/watch?v=HaTChgbnw5E&list=PLrrgFyE6PtlaCixUxJPM0Y9Peye6iCewH&index=3