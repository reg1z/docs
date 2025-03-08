---
tags:
  - linux
  - monitoring
  - systemd
date: 2025-03-07
---
# systemd-journald
*journald* is great for local log collection. It provides centralized logging for the kernel, system services, and applications.

Logs produced by journald can be digitally signed, when configured.

## journalctl
Use the `journalctl` command to query these logs.

- `journalctl -u name.service` → View logs for a specific service.
- `journalctl -b` → View logs since the last boot.
- `journalctl -f` → View logs in real-time.

## Syslog compatibility

- Logs collected by journald can be imported into [[syslog]] with the `/run/systemd/journal/syslog` socket.
- You can also enable a setting within `journald.conf` to automatically forward them to syslog.


## Notable locations

### Configuration Files

- `/etc/systemd/journald.conf` → main config
- `/etc/systemd/journald.conf.d/` → for drop-in configurations that will override the main config
- ⭐ To apply config changes use `sudo systemctl restart systemd-journald
`

## Storage

- **volatile storage** → `/run/systemd/journal` → where journald temporarily stores log data in RAM
	- part of the **tmpfs** filesystem
	- used if **persistent storage** is not enabled
	- using RAM allows for faster operations compared to on disk
	- Contains:
		- `/run/systemd/journal/syslog` → syslog socket
		- **State Files:** Track the current state of log writing, cursor positions, etc.
- **persistent storage** → `/var/log/journal` → where journald will permanently store logs if enabled

