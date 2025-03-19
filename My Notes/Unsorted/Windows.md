---
tags:
  - windows
  - operatingSystems
date: 2025-03-18
---
# Windows

> [!tip]- Links and Sources
> - [Wikipedia - Architecture of Windows NT](https://en.wikipedia.org/wiki/Architecture_of_Windows_NT)
> - [Wikipedia - Session Manager Subsystem (smss.exe)](https://en.wikipedia.org/wiki/Session_Manager_Subsystem)

> [!abstract]- Random Points & Reminders
> **Sessions**
> - Session 0 → OS (kernel) Session
> - Session 1 → User Session (Session 1 will be for the **1st *logged-in* user** to the system)

## Child Notes

### Powershell
- 🌠 [From Bash to PowerShell](My%20Notes/Unsorted/From%20Bash%20to%20PowerShell.md) → Mapping typical `bash` commands to their `pwsh` (PowerShell) equivalents.

### Windows Core
- [Windows Event Logs](My%20Notes/Unsorted/Windows%20Event%20Logs.md)
- [Windows Sysinternals](My%20Notes/Unsorted/Windows%20Sysinternals.md) → A suite of 70+ tools for digging deep into the Windows system.


## In Progress

### Bullet Notes

#### Core Windows Processes

- System
	- parent process: system idle process (0)
	- The PID for System is always 4
	- Runs only in kernel-space
		- See [MS docs - kernel mode and user mode](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/user-mode-and-kernel-mode)
	- System threads don't have a user process address space.
	- There should only every be a single instance
- smss.exe - session manager subsystem
	- parent process: System
	- the first user-mode process started by the kernel
	- starts session 0
		- csrss.exe
		- wininit.exe
	- starts session 1
		- csrss.exe
		- winlogon.exe
	- *"SMSS is also responsible for creating environment variables, virtual memory paging files and starts winlogon.exe (the Windows Logon Manager)."*
	- self-terminates
- csrss.exe - client server runtime process
	- *"This process is also responsible for making the Windows API available to other processes, mapping drive letters, and handling the Windows shutdown process. You can read more about this process [here](https://en.wikipedia.org/wiki/Client/Server_Runtime_Subsystem)."*
- wininit.exe - windows initialization process
	- launches
		- services.exe
		- lsass.exe
		- lsaiso.exe
			- you will only see this process if credential guard is enabled
- services.exe - service control manager (SVM)
	- only a single instance of this should ever be running at once.
	- handles system services.
	- maintains a database that is queriable with the built-in windows tool, `sc.exe`
	- *"This process is the parent to several other key processes: svchost.exe, spoolsv.exe, msmpeng.exe, and dllhost.exe, to name a few. You can read more about this process [here](https://en.wikipedia.org/wiki/Service_Control_Manager)."*
- svchost.exe - service host
	- services running here are implemented as `.dll` files.
		- *"The DLL to implement is stored in the registry for the service under the `Parameters` subkey in `ServiceDLL`. The full path is `HKLM\SYSTEM\CurrentControlSet\Services\SERVICE NAME\Parameters`."*
	- a legitimate instance of this process is launched with the -k flag
		- *"The -k parameter is for grouping similar services to share the same process. This concept was based on the OS design and implemented to reduce resource consumption. Starting from **Windows 10 Version 1703,** services grouped into host processes changed. On machines running more than 3.5 GB of memory, each service will run its own process. You can read more about this process [here](https://en.wikipedia.org/wiki/Svchost.exe)."*
	- *"Since svchost.exe will always have multiple running processes on any Windows system, this process has been a target for malicious use. Adversaries create malware to masquerade as this process and try to hide amongst the legitimate svchost.exe processes. They can name the malware svchost.exe or misspell it slightly, such as scvhost.exe. By doing so, the intention is to go under the radar. Another tactic is to install/call a malicious service (DLL)."*
- lsass.exe - local security authority subsystem service
- winlogon.exe
	- handles the **secure attention sequence** (SAS)
	- [Wikipedia - Winlogon](https://en.wikipedia.org/wiki/Winlogon)
	- starts userinit.exe
		- [MS docs - userinit](<https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc939862(v=technet.10)?redirectedfrom=MSDN>)
- explorer.exe - windows explorer
	- *"As mentioned previously, the Winlogon process runs userinit.exe, which launches the value in `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\Shell`. Userinit.exe exits after spawning explorer.exe. Because of this, the parent process is non-existent."*


