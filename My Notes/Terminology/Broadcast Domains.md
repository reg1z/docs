---
tags:
  - terminology
  - networking
  - subnetting
date: 2025-04-04
---
# Broadcast Domains

> [!quote]+ From [pfSense docs → Broadcast Domains](https://docs.netgate.com/pfsense/en/latest/network/broadcast-domains.html)
> A broadcast domain is the portion of a network sharing the same layer 2 segment. Broadcast messages from hosts are sent to every port in their broadcast domain, thus hosts inside a broadcast domain can reach each other directly. For example hosts can use ARP or NDP to locate neighbors within a broadcast domain and communicate directly at layer 2 without involving an intermediate gateway router.
> 
> In a network with a single switch without VLANs, the broadcast domain is that entire switch. In a network with multiple interconnected switches without the use of VLANs, the broadcast domain includes all of those switches. When using VLANs, each VLAN is typically its own broadcast domain. The exact size of the broadcast domain in that case varies depending on how many access ports are in the VLAN, along with interconnected switches (trunked, stacked, etc).
> 
> ...

See also:

- [Wikipedia - Broadcast domain](https://en.wikipedia.org/wiki/Broadcast_domain)
