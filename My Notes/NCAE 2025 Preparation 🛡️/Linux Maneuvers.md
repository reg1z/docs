# Linux Maneuvers
Specific techniques worthy of practice. Particularly when it comes to cybersecurity.

## Useful Maneuvers

- Clearing memory caches with [Linux Drop Caches](../Unsorted/Linux%20Drop%20Caches.md)

## Practice Maneuvers
Techniques players might want to practice for game day.

SSH
- SSH Proxying (Port Forwarding)
- Copying files via `scp`
	- recursive option

Network Security Monitoring
- Packet Capture
	- Wireshark, etc.
- Packet Analysis
	- Manually...
	- Zeek

SSL certificate authority

## Things that'll need to get done

- Int DNS
- Ext DNS
- DB
	- backups
- DNS

Pair together those with complementary experiences. Those who know some of the above with those that know less.

## What Regis is focusing on:

- Setting up logs
	- learning systemd
		- config [systemd-journald](../Unsorted/systemd-journald.md)
		- [systemd-timers](../Unsorted/systemd-timers.md)
	- config [rsyslog](../Unsorted/rsyslog.md)
	- config them to hide logs in a location deep in the linux filesystem
	- config multiple other locations to send trash logs to.

## Other things we may want to do
- If the desktop environment is available, disable auto-lock?
- Check out that detection script from one of those gitlab repos. There was one that detects users logged into a tty (or something else similar) that shouldn't actually be logged in. We could have a script like that, which would then trigger an alert. If that alert gets triggered, we could perhaps send automatic responses to whatever process/shell that user is running on. Something like spamming out their console with "gitrektgitrektgitrekt", wiping any artifacts they've generated, shutting down their session/connections, etc.
- Timers
	- ⭐ How do we prevent manipulation of the system clock?
	- Use systemd timers instead. They're better.
	- Alternatives
		- backup bash / python scripts with similar functionality?
		- is cron actually worth the risk? It has a small attack surface, but could affect the entire system.
	- Set up a timer/trigger → if a certain timer is somehow disabled / turned off, have a trigger go off that would start an emergency backup timer script that could either perform the same function as the timer temporarily, or restore the functionality of the systemd timer.
- In our first 30-60 mins of setup
	- get scripts copied to local hosts with the clipboard. Wipe the clipboard. Setup encrypted backups of scripts?

## Directories worth monitoring

- Logs
- configuration files
- sudo
- passwd
- shadow
- hosts (dns)
- network configurations

## Common Sense

> [!tip]+ Security Best Practices
> Regardless of which system you use, several best practices apply:
> 
> 1. **Principle of least privilege**: Run scheduled tasks with the minimum permissions necessary
> 2. **Comprehensive logging**: Ensure all task outputs are logged and monitored
> 3. **Input validation**: Carefully validate any external inputs used in scheduled tasks
> 4. **Script security**: Use absolute paths, avoid shell expansions when possible, and properly quote variables
> 5. **Regular audits**: Periodically review all scheduled tasks