---
tags:
  - NCAE
date: 2025-03-09
---
# Summary Document

---

# Logging approach

On other endpoints
1. Create accounts on endpoints
2. configure endpoints for ssh
	1. OR, just use the default credentials to get ssh keys over
3. receive public keys
4. ??? Other setup ???
5. Clear bash history
6. Clear clipboard

On log aggregator
1. Generate 20 ssh key pairs
2. send public keys → 2 to each endpoint

---
# Questions for the group

## Locations

### ENCRYPTION - 🚨
- SSH → Where do we want to store SSH keys
	- Log aggregation server? 5 different private keys? Each in different locations?
	- Where on individual hosts?
- Logs → Where to store OpenSSL encryption keys + init vectors?
	- They will have to be on every logged endpoint.
	- Or should we just do pull-based logging



### LOG LOCATIONS - 🚨



### WHAT ELSE?
- We need to make sure the following are cleared on each host before the red team begins:
	- bash history wiped (and perhaps disabled)
	- clipboard cleared of all contents
		- ensure clipboard contents are only in the buffer for 15-20 seconds?


# Individual Hosts

All
- iptables / ufw




## Network

The scripts I've targeted here (poll2.sh, rotatePoll2.sh, central-sshConfigSetup2.sh, central-sshMake2.sh) have static lists of IPs within. Parts of their functionality have been designed with these IPs in mind. I would like you to change these files, preserving existing functionality, while adding some more IPs to the static list. These new IPs should have the same existing functionality provided to them. Thank you.

I want to replace the existing "external-kali" host/IP with all of these hosts/IPs representing individual external-kali boxes. Each host should have 2 new SSH key pairs generated for them. These key pairs should also each relocated to a unique, inconspicuous location under the /home/$LOGGINGUSER directory (just like with all the other existing key pairs). The name of each should be mapped as follows:
external-kali-1 → 172.18.15.161
external-kali-2 → 172.18.15.162
external-kali-3 → 172.18.15.163
external-kali-4 → 172.18.15.164
external-kali-5 → 172.18.15.165
external-kali-6 → 172.18.15.166


I want to replace the existing "internal-kali" host/IP with all of these hosts/IPs representing individual internal-kali boxes. Each host should have 2 new SSH key pairs generated for them. These key pairs should also each relocated to a unique, inconspicuous location under the /home/$LOGGINGUSER directory (just like with all the other existing key pairs). The name of each should be mapped as follows:
internal-kali-1 → 192.168.16.41
internal-kali-2 → 192.168.16.42
internal-kali-3 → 192.168.16.43
internal-kali-4 → 192.168.16.44
internal-kali-5 → 192.168.16.45
internal-kali-6 → 192.168.16.46

