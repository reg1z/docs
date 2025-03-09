---
tags:
  - NCAE
date: 2025-03-08
---
# Team Strategy


## Logs

> [!info]+ Relevant Notes
> - [systemd](systemd.md)
> - [systemd-timers](systemd-timers.md)
> - [systemd-journald](systemd-journald.md)
> - [rsyslog](rsyslog.md)
> - [logrotate](logrotate.md)

### Potential Tools

- logrotate
- logcheck - "Logcheck is a security monitoring tool that scans system log files for suspicious or abnormal entries and emails reports to administrators. It works by analyzing logs against sets of rules that define normal/expected log entries, violations, and security concerns."
- 

### Strat - Logging

#### Services & Tools used

- `systemd-journald` as local logging solution → using **imjournal** module, will be imported as json into `rsyslog` → sent to external host.
	- They can be audited locally in the efficient journald format, THEN imported to rsyslog WHEN NEEDED to be integrated with our improvised SIEM?
	- **Comments**
		- This should hopefully work for all hosts. We should have a backup in case there is a system not using rsyslog or systemd-journald.
- 

#### Config Locations

-  **journald**
	- `/etc/systemd/journald.conf`
	- `/etc/systemd/journald.conf.d`
- **rsyslog**
	- 

## Database

> [!info]+ Relevant Notes

## Networking

> [!info]+ Relevant Notes

### DNS