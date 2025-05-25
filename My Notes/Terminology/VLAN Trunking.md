---
tags:
  - terminology
  - networking
  - subnetting
date: 2025-04-04
---
# VLAN Trunking

> [!quote]+ [From pfSense docs → VLAN Terminology](https://docs.netgate.com/pfsense/en/latest/vlan/terminology.html)
> Trunking refers to a means of carrying multiple VLANs on the same physical switch port. The frames leaving a trunk port are marked with an 802.1Q tag in the header, enabling the connected device to differentiate between multiple VLANs. Trunk ports are used to connect multiple switches, and for connecting any devices that are capable of 802.1Q tagging and require access to multiple VLANs. This is commonly limited to the firewall or router providing connectivity between VLANs, in this case, the firewall running pfSense® software, as well as any connections to other switches containing multiple VLANs.

See also:

- [pfSense docs → VLANs and Security](https://docs.netgate.com/pfsense/en/latest/vlan/security.html)
	- When configuring VLAN trunking, you should not use the default VLAN id (1) 