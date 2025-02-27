# Preparing for a Blue Team Competition as a Beginner

> See [NCAE 2025](../NCAE%202025%20Preparation%20🛡️/NCAE%202025.md) for comprehensive links to the team's prepatory documents.

This February, I found 

There are **key skills** one should be familiarized with before expecting *competitive* results in a Red vs. Blue team engagement. I am not saying one *shouldn't compete if the skills aren't yet in their toolbelt*—these engagements are great ways to acquire them—but, if you plan to *win* preparation, study, and regular practice are an absolute must.

The NCAE is a competetion targeted at those new to cybersecurity competitions. So, I felt a need to compile a list of these skills. The knowledge Keep in mind, there are a staggering amount of approaches to take in a Blue Team engagement like the NCAE. This list is targeted at those wanting an idea of the "bare minimum."

⭐ 
### Some Tips
- Don't consider *too many* tools for the job all at once. You will experience [Choice Paralysis](../unsorted/Choice%20Paralysis.md). At times it's best to pick something just to get experience with it. If it's not working out, go to the next thing on the list.


### The Skills
- Research Skills. Not necessarily academic research. Knowing how to tactically prompt search engines and various AI tools can get you information you need fast. Knowing when to question results is just as important.
- There are several widely known "core" sites participants frequent.
- OS / Environment Proficiency
	- Linux Specific
		- Navigating the Linux Command-line and File structure
		- Bash syntax
		- Common commands
		- Service configuration
			- systemctl / systemd
		- Networking in Linux
			- DNS
			- Opening/closing ports
			- Routing
	- Windows 

---

```
Echotango + w33t notes:

- You are root 
- There is no GUI.  
- There is no locking yourself out bcuz proxmox 
- Ssh 
    - Ssh config 
    - Ssh proxying 
- Common service configs 
    - Nginx 
    - Databases (SQL, postgres, flask) 
    - Bind DNS 
    - Certificate services – certbot 
        - --dry-run DO THIS BEFORE RATE LIMITS IMPOSED 
- Monitoring 
    - Syslog? 
    - Wazuh? Maybe not 
- Ansible 
    - Add hosts to ansible inventory 
- `lsof -i –n` 
- `Lsof –p <process id> #open file with process id of <>`
- Ls /proc to see the process id folder 
- Run srtrings on exe file on memory  
- Pay attention to where the file was invoked at to look in the `/proc/<processid>/cmdline` ##cat this file 
- Come up with a triage of IoCs.  
- Search all hosts for IoCs. For the SAME IoCs you've found on individual hosts. 
- Runbook?? For IoCs 
- Netstat and ss comand are looking for ioc 
- IPtables deep dive wouldn’t be a bad idea. Nmap scan deturrent  
    - Localhost firewall per host??? 
    - We need a way to share passwords  
    - Ssh keys?? Add pub key to auth_keys 
    - Practice enviroment???? 
    - Digital ocean for one box for the enviorment AZure terraform few bucks... 

Discord 

Black team – they are there to help remember this is a beginner level comp and you are here to learn they are here to teach  

Red team – they are there to make fun with you   

Potential Roles 
- Someone watching the attacks 
- Could a less experienced team member "get the 3 checks" as fast as possible? 
    

Questions 
- How do you profile the scoring engine? 
    - Looking at http logs 
    - Looking for keywords for certain exploits ---> drop those packets 

Links: 
- https://overthewire.org/wargames/bandit/
- https://redsiege.com/tools-techniques/2019/05/logging-passwords-on-linux/

Misc. Tips 

- Lsof command 
- Absolute Musts: 
    - Take backups immediately 
    - User / group setup script 
        - Memorize your own unique passwords 
    - Least privileges 
        - File/folder roles 
    - Vulnerability Scan 
    - Backups   
    - Monitoring 
        - Wazuh – (anihacc had set up something) 
    - SSH config
```