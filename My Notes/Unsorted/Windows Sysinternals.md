---
tags:
  - windows
date: 2025-03-19
---
# Windows Sysinternals
*Sysinternals contains 70+ tools. The list presented here is non-exhaustive.*

> [!tip]- Links and Sources
> - Microsoft Docs
> 	- [MS Learn - Sysinternals](https://learn.microsoft.com/en-us/sysinternals/)
> 	- [MS Learn - Sysinternals Suite (Downloads)](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite)
> 	- [MS Learn - Troubleshooting with the Windows Sysinternals Tools (Official Guide to the Sysinternals Tools)](https://learn.microsoft.com/en-us/sysinternals/resources/troubleshooting-book)
> - Wikipedia
> 	- [Wikipedia - Sysinternals](https://en.wikipedia.org/wiki/Sysinternals)
> - TryHackMe
> 	- [THM - Sysinternals](https://tryhackme.com/room/btsysinternalssg) (SOC Level 1 Learning Pathway)

#### File and Disk Utilities

- **sigcheck**
- **streams**
- **sdelete**

#### Networking Utilities

- **tcpview**

#### Process Utilities

- **autoruns** → *"This utility, which has the most comprehensive knowledge of auto-starting locations of any startup monitor, shows you what programs are configured to run during system bootup or login, and when you start various built-in Windows applications like Internet Explorer, Explorer and media players. These programs and drivers include ones in your startup folder, Run, RunOnce, and other Registry keys. **Autoruns** reports Explorer shell extensions, toolbars, browser helper objects, Winlogon notifications, auto-start services, and much more. Autoruns goes way beyond other autostart utilities."*
	- *"This is a good tool to search for any malicious entries created in the local machine to establish Persistence."*
- **Procdump**
- **Process Explorer**
- **Process Monitor**
- **PsExec**

#### Security Utilities

- **Sysmon** → *"System Monitor (Sysmon) is a Windows system service and device driver that, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log. It provides detailed information about process creations, network connections, and changes to file creation time. By collecting the events it generates using Windows Event Collection or SIEM agents and subsequently analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network."*

#### System Information

- **WinObj** → *"...a 32-bit Windows NT program that uses the native Windows NT API (provided by NTDLL.DLL) to access and display information on the NT Object Manager's name space."*

#### Miscellaneous

- **BgInfo**
- **RegJump**
- **Strings**