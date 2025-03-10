---
tags:
  - NCAE
date: 2025-03-09
---
# NCAE AI Prompt

```markdown
For the duration of this conversation, please keep the following information in mind.

I seek assistance on configuring a particular network environment. This environment is designed for a blue team competition. We are the blue team. The goal is for us, as the blue team, to minimize attack surface, monitor, and prevent threats. We are scored on certain criteria such as the uptime and availability of services with the scoring infrastructure over the course of the 7-hour competition.

The key threat is the red team, who will have pre-configured vulnerabilities and backdoors into our internal network prior to the start of the competition. We'll be at risk of unauthorized access, malware, lateral movement, privesc, and potentially DoS. We currently are unaware of the full breadth of threats we'll be subject to. Aside from the provided scope, there are no compliance / competition rules restricting certain actions.

I MIGHT have attached an image of the network topology, but may not have. Regardless, here are other crucial details:

**Our Team Number**

- ⭐ We are team number: 56
	- Within the IP addresses listed below, please replace instances of the variable "t" with our team number.

**Other Details:**

- The environment is hosted on a proxmox server we will be cloud-connected to. All endpoints are hosted on this proxmox instance.
- Each host will have no more than 2GB of ram.
- The Microtik router has only 1GB of ram.
- Each host will have no more than a single processor core/thread.
- We have noVNC access to all hosts.
- We have SPICE access to all hosts except the Microtik Router.
- "t" in the screenshot is a variable representing our team number, which will comprise some of our network/host addresses. .
- IPv6 is likely to be unused. We will likely disable it if so.
- We will have access to the external internet via the link between the Microtik and Hackathon routers. It has a max bandwidth of 25Mb. The route to the external internet would have to be manually set up.
- It might not be possible to remediate vulnerable hosts with the regular channels (official updates, etc). Even with an external network connection, out-of-date hosts could reject updates if there is no secure way to download packages.
- We will only have 30 minutes to 1 hour to setup the hosts at the start of the competition.
- The first half of the competition lasts for 3 hours—there is then an hour lunch break—then the second half of the competition lasts for another 3 hours.
- We have to manually configure network settings/IPs/routes ourselves.
- We only are allowed to control the hosts/endpoints listed here.

- **Endpoints in our control:**
	- **Both Sides**
		- **Default Gateway/Team Router**: is a Microtik Router - RouterOS version 7.17.1.
			- Network interfaces
				- eth0: 172.18.13.t (external)
				- eth1: 192.168.t.1 (internal)
	- **External Network** (IP range 172.18.0.0/16)
		- External Kali VM:
			- IP: 172.18.15.t
			- OS: Kali version 2021.1
		- Shell / FTP VM:
			- IP: 172.18.14.t
			- OS: UNKNOWN Linux Distro
			- Services: UNKNOWN.
	- **Internal Network** (IP range 192.168.t.0/24)
		- Internal Kali VM:
			- IP: 192.168.t.10
			- OS: Kali version 2021.1
		- Web Server:
			- IP: 192.168.t.5
			- OS: UNKNOWN Linux Distro, but possibly Ubuntu LTS Focal Fossa.
			- Services: UNKNOWN web server service. nginx, and apache2 are possibilities, but we are unsure.
		- Database:
			- IP: 192.168.t.7
			- OS: UNKNOWN Linux Distro
			- Services: UNKNOWN. Could be MySQL, PostgreSQL, flask, etc. Not sure.
		- DNS:
			- IP: 192.168.t.12
			- OS: UNKNOWN Linux Distro
			- Services: UNKNOWN. Likelist DNS server is bind.
		- Backup Server:
			- IP: 192.168.t.15
			- OS: UNKNOWN Linux Distro
			- Services: UNKNOWN
- **Black Team Endpoints**
	- **External Network** (IP range 172.18.0.0/16)
		- Scoring Engines
			- Nothing else known.
		- DNS
			- IP: 172.18.0.12
			- Nothing else known.
		- Remote Shell
			- IP: 172.18.13.15
			- Nothing else known.
		- Certificate Authority
			- IP: 172.18.0.38
			- Nothing else known.
		- Blue Team Jumphost
			- Nothing else known, but we will be allowed to `ssh` into our internal network through our local (physical) machines.
		- There could be other hosts managed by the Black Team here now that are a part of the competition, but we have not been given this information.

Thank you for your consideration. I deeply appreciate your efforts!
```