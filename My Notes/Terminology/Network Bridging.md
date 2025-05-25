---
tags:
  - terminology
  - networking
date: 2025-04-04
---
# Network Bridging

> [!quote]+ [From pfSense docs → Bridging](https://docs.netgate.com/pfsense/en/latest/bridges/index.html)
> Normally each interface on the pfSense® firewall represents its own broadcast domain with a unique IP subnet. In some circumstances it is desirable or necessary to combine multiple interfaces onto a single broadcast domain, where two ports on the firewall will act as if they are on the same switch, except traffic between the interfaces can be controlled with firewall rules. Typically this is done so multiple interfaces will act as though they are on the same flat network using the same IP subnet and so that clients all share broadcast and multicast traffic.
> 
> Certain applications and devices rely on broadcasts to function, but these are found more commonly in home environments than corporate environments. For a practical discussion, see [Bridging and wireless](https://docs.netgate.com/pfsense/en/latest/wireless/bridges.html).
> 
> For services running on the firewall, bridging can be problematic. Features such as limiters, Captive Portal, and transparent proxies require special configuration and handling to work on bridged networks. Specifically, the bridge itself must be assigned and the only interface on the bridge with an IP address must be the assigned bridge. Also, in order for these functions to work, the IP address on the bridge must be the address used by clients as their gateway. These issues are discussed more in-depth in [Bridging interoperability](https://docs.netgate.com/pfsense/en/latest/bridges/interoperability.html).
> 
> ...
> 
> There are two distinct types of bridges: **Internal bridges** and **Internal/external bridges**. Internal bridges connect two local interfaces such as two LAN interfaces or a LAN interface and a wireless interface. Internal/external bridges connect a LAN to a WAN resulting in what is commonly called a “transparent firewall”.

See also:

- [pfSense docs → Bridging and wireless](https://docs.netgate.com/pfsense/en/latest/wireless/bridges.html)