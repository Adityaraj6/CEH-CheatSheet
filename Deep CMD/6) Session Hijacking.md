Tools Used
1) OWASP ZAP (here the attacker itsef is windows host)
	1) in chrome -> settings -> system -> proxy settings -> LAN settings -> check proxy server -> add attacker IP address and port to 8080 -> OK
	2) On the main windows click do not persist
	3) After the main screen appears click the `+`  symbol 
	4) For ZAP to work as a proxy go to Tools -> options -> then search for Local Proxies -> add attacker address -> DO NOT CHANGE THE PORT
	5) Using orange circle set a break point
	6) go to the website we want to capture request on
	7) capture request and click **submit and step to next request or response**  change the web site to your wanted website  and done

https://www.youtube.com/watch?v=5jc3Q0UG7lg&list=PLrrgFyE6PtlaCixUxJPM0Y9Peye6iCewH&index=6