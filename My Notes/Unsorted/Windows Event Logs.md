---
tags:
  - windows
  - monitoring
  - logging
date: 2025-03-19
---
# Windows Event Logs

> [!tip]- Links and Sources
> - TryHackMe
> 	- [THM - Windows Event Logs](https://tryhackme.com/room/windowseventlogs)

> [!quote]+ THM - Elements of Windows Event Logs
> - **System Logs:** Records events associated with the Operating System segments. They may include information about hardware changes, device drivers, system changes, and other activities related to the device.
> - **Security Logs:** Records events connected to logon and logoff activities on a device. The system's audit policy specifies the events. The logs are an excellent source for analysts to investigate attempted or successful unauthorized activity.
> - **Application Logs** :Records events related to applications installed on a system. The main pieces of information include application errors, events, and warnings.
> - **Directory Service Events:** Active Directory changes and activities are recorded in these logs, mainly on domain controllers.
> - **File Replication Service Events:** Records events associated with Windows Servers during the sharing of Group Policies and logon scripts to domain controllers, from where they may be accessed by the users through the client servers.
> - **DNS Event Logs:** DNS servers use these logs to record domain events and to map out
> - **Custom Logs:** Events are logged by applications that require custom data storage. This allows applications to control the log size or attach other parameters, such as ACLs, for security purposes.

## 3 Predominant Ways to View Event Logs
### Event Viewer (gui)

- It's an mmc snap-in: `eventvwr.msc`

### Wevtutil.exe (cmd prompt)
> *"...enables you to retrieve information about event logs and publishers. You can also use this command to install and uninstall event manifests, to run queries, and to export, archive, and clear logs."*

Commands:
![](../../assets/images/Pasted%20image%2020250319105409.png)

### Get-WinEvent (powershell)
> "...gets events from event logs and event tracing log files on local and remote computers."
> 
> "**Note**: The **Get-WinEvent** cmdlet replaces the **Get-EventLog** cmdlet."


## Bullet Notes

- Sysmon
	- 27 types of event IDs
- **Event ID:** "This is a predefined numerical value that maps to a specific operation or event based on the log source. This makes Event IDs not unique, so `Event ID 4103`... \[will have a specific meaning for a specific log source, but] will have an entirely different meaning in another \[source's] event log."
- **Event Task Categories:** Event/Log sources define the **Task Category** of particular events (and their associated IDs).
- 