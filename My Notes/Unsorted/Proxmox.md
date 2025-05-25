---
tags:
  - virtualization
  - containerization
  - proxmox
date: 2025-03-21
---
# Proxmox
An open-source virtualization and containerization platform.

> [!abstract]+ Links and Sources
> - Proxmox Official
> 	- [Proxmox Forums](https://forum.proxmox.com/)
> 	- Wiki
> 		- [Main Page](https://pve.proxmox.com/wiki/Main_Page)
> - YouTube
> 	- [Learn Linux TV - Proxmox VE Playlist](https://www.youtube.com/playlist?list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo)
> 	- 

Competitors

- VMware vSphere / ESXi
- Red Hat Virtualization / oVirt → reaching EOL in 2026
- XCP-ng + Xen Orchestra

Misc. Info

- Proxmox is based on **Debian**.
- You generally only want a **single gateway** set in proxmox even when having the server configured with multiple interfaces/subnets/vlans. You can leave this field empty for most interfaces beyond the first (generally).


Misc. Config Files

- `/etc/pve/firewall/cluster.fw` ← Firewall configuration file

Misc. Files

- `/var/lib/vz/template/iso` ← .iso images uploaded to a node are stored here

## User Management and Authentication Realms

Authentication Realms make things different vs. typical Linux administration.

- **Proxmox VE authentication server** → WebGUI-exclusive user account. Has no ability to operate the shell console of a node when configured using this realm.
- **Linux PAM standard authentication** → The only time you need to worry about configuring Linux users in the traditional way on a particular proxmox node is when you are creating a user in the **pam** realm.
- **LDAP** → ...
- **Microsoft Active Directory** → ...

Users are typically identified in the form of: `user@realm`

### User Configuration files

- `/etc/pve/user.cfg`
- `/etc/pve/domains.cfg`
	- *"As **Proxmox VE users are just counterparts for users existing on some external realm**, the realms have to be configured in /etc/pve/domains.cfg."*
		- For the PVE Authentication Server itself, users are self-contained and managed by the proxmox virtual environment exclusively.

### Realm "Counterpart" users

#### Proxmox VE Authentication Server
> This is a unix like password store (/etc/pve/priv/shadow.cfg). Password are encrypted using the SHA-256 hash method. This is the most convenient method for small (or even medium) installations where users do not need access to anything outside of Proxmox VE. In this case users are fully managed by Proxmox VE and are able to change their own passwords via the GUI. 

#### pam
When using the **pam authentication realm**, a corresponding user must be configured on the relevant proxmox endpoint(s). The account must be individually configured on each node the VE user wishes to access

From the proxmox docs:
```bash
useradd heinz
passwd heinz
groupadd watchman
usermod -a -G watchman heinz
```




## Proxmox CLI


### Qemu Manager

- `qm` → qemu manager
	- `list`
	- `start <id>`
	- `shutdown <id>`
	- `reboot <id>` (graceful)
	- Potentially destructive, but can help fix wonky VMs
		- `stop <id>`
		- `reset <id>` (not graceful)
	- Configuration
		- `qm config <id>` → list the current configuration of the target VM
		- `set --<optionX> <id>` → set options

#### Passing through physical hard drives...
You can pass through physical hard drives (and other hardware devices) to proxmox.

These examples use disks by their IDs—this is more stable across reboots vs using `/dev/sdX` (these can change between boots):

- `qm set 555 -scsi1 /dev/disk/by-id/ata-ST000,cache=none,...`
- `qm set 555 -scsi2 /dev/disk/by-id/ata-ST001,cache=none,...`


### Proxmox Container Toolkit

- `pct` → proxmox container toolkit
	- commands are fairly similar
	- `enter <id>` → opens a terminal session in the target container



## PCI Passthru (standard single GPU / device passthru)
See → [Proxmox Wiki - PCI Passthrough](https://pve.proxmox.com/wiki/PCI_Passthrough)
- Great Video: [YouTube - NetworkwithChris - Configure GPU Passthrough on Proxmox Step-by-Step (IOMMU Guide)](https://www.youtube.com/watch?v=Il6HhOCfDjI)

Requirements

- CPU that supports hardware virtualization + IOMMU.
- Motherboard with virtualization + IOMMU (Input Output Memory Management Unit) support.
	- Has these settings enabled within the BIOS.
- Depending on whether you'll be passing through a GPU, there might be some misc. tinkering to do with certain settings (see the wiki link above), etc.

Caveats

- Makes the PCI device / GPU *exclusively* available to the target VM.