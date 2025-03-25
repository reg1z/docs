---
tags:
  - windows
  - logging
  - monitoring
date: 2025-03-20
---
# Sysmon
A Windows Sysinternals module for logging the activity of core Windows systems. System activity is logged to the Windows Event Log. Once configured, it remains persistent across reboots.

## Bullet Notes

Events

- ID 1 → process creation
- ID 3 → network connection
- ID 7 → image loaded
	- i.e. Looks for **DLLs** loaded by processes.
	- This event ID can cause a high system load.
- ID 8 → CreateRemoteThread
	- monitors for processes injecting code into other processes.
- ID 11 → file created
- ID 12/13/14 → registry events
- ID 15 → FileCreateStreamHash
- ID 22 → DNS Event

