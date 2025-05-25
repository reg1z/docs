---
tags:
  - cybersecurity
  - traffic-analysis
  - networking
date: 2025-03-18
---
# Traffic Analysis with Wireshark

> [!tip]- Links & Sources
> - [wireshark.org](https://www.wireshark.org/)
> - [THM - Wireshark: Traffic Analysis](https://tryhackme.com/room/wiresharktrafficanalysis)



## Detecting Specific Behaviors
### nmap scans

*"TCP Flags in a nutshell..."*

| **Notes**                                                                                | **Wireshark Filters**                                                      |
| ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Global search.                                                                           | - `tcp`<br>- `udp`                                                         |
| - Only SYN flag.<br>- SYN flag is set. The rest of the bits are not important.           | - `tcp.flags == 2`<br>- `tcp.flags.syn == 1`                               |
| - Only ACK flag.<br>- ACK flag is set. The rest of the bits are not important.           | - `tcp.flags == 16`<br>- `tcp.flags.ack == 1`                              |
| - Only SYN, ACK flags.<br>- SYN and ACK are set. The rest of the bits are not important. | - `tcp.flags == 18`<br>- `(tcp.flags.syn == 1) and (tcp.flags.ack == 1)`   |
| - Only RST flag.<br>- RST flag is set. The rest of the bits are not important.           | - `tcp.flags == 4`<br>- `tcp.flags.reset == 1`                             |
| - Only RST, ACK flags.<br>- RST and ACK are set. The rest of the bits are not important. | - `tcp.flags == 20`<br>- `(tcp.flags.reset == 1) and (tcp.flags.ack == 1)` |
| - Only FIN flag<br>- FIN flag is set. The rest of the bits are not important.            | - `tcp.flags == 1`<br>- `tcp.flags.fin == 1`                               |

TCP Scans

- Connect Scans
- SYN Scans

UDP Scans

---

### ARP Poisoning / Spoofing
Manipulation of the "IP to MAC Address Table" via the sending of malicious ARP packets (MITM Attack).

> [!quote]+ ARP in a nutshell (THM)
> - Works on the local network
> - Enables the communication between MAC addresses
> - Not a secure protocol
> - Not a routable protocol
> - It doesn't have an authentication function
> - Common patterns are request & response, announcement and gratuitous packets.



| **Notes**                                                                                                                                                                                                                                          | **Wireshark filter**                                                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Global search                                                                                                                                                                                                                                      | - `arp`                                                                                                                                                                                                                                                |
| "ARP" options for grabbing the low-hanging fruits:<br><br>- Opcode 1: ARP requests.<br>- Opcode 2: ARP responses.<br>- **Hunt:** Arp scanning<br>- **Hunt:** Possible ARP poisoning detection<br>- **Hunt:** Possible ARP flooding from detection: | - `arp.opcode == 1`<br><br>- `arp.opcode == 2`<br><br>- `arp.dst.hw_mac==00:00:00:00:00:00`<br><br>- `arp.duplicate-address-detected or arp.duplicate-address-frame`<br><br>- `((arp) && (arp.opcode == 1)) && (arp.src.hw_mac == target-mac-address)` |

Identifying between 2 spoofed packets is up to an analyst:
![](../../assets/images/Pasted%20image%2020250318090624.png)


---

*There are many ways to detect types of hosts in addition to IP and MAC addresses...*

*Traffic Types*
- *DHCP*
- *NetBIOS (NBNS)*
- *Kerberos*


### DHCP

**DHCP investigation in a nutshell:**

| **Notes**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **Wireshark Filter**                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Global search.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | - `dhcp` or `bootp`                                                                                                                                                                                                                     |
| Filtering the proper DHCP packet options is vital to finding an event of interest.   <br>  <br><br>- **"DHCP Request"** packets contain the hostname information<br>- **"DHCP ACK"** packets represent the accepted requests<br>- **"DHCP NAK"** packets represent denied requests<br><br>Due to the nature of the protocol, only "Option 53" ( request type) has predefined static values. You should filter the packet type first, and then you can filter the rest of the options by "applying as column" or use the advanced filters like "contains" and "matches". | - Request: `dhcp.option.dhcp == 3`<br><br>- ACK: `dhcp.option.dhcp == 5`<br><br>- NAK: `dhcp.option.dhcp == 6`                                                                                                                          |
| **"DHCP Request"** options for grabbing the low-hanging fruits:<br><br>- **Option 12:** Hostname.<br>- **Option 50:** Requested IP address.<br>- **Option 51:** Requested IP lease time.<br>- **Option 61:** Client's MAC address.                                                                                                                                                                                                                                                                                                                                      | - `dhcp.option.hostname contains "keyword"`                                                                                                                                                                                             |
| **"DHCP ACK"** options for grabbing the low-hanging fruits:<br><br>- **Option 15:** Domain name.<br>- **Option 51:** Assigned IP lease time.                                                                                                                                                                                                                                                                                                                                                                                                                            | - `dhcp.option.domain_name contains "keyword"`                                                                                                                                                                                          |
| **"DHCP NAK"** options for grabbing the low-hanging fruits:<br><br>- **Option 56:** Message (rejection details/reason).                                                                                                                                                                                                                                                                                                                                                                                                                                                 | As the message could be unique according to the case/situation, It is suggested to read the message instead of filtering it. Thus, the analyst could create a more reliable hypothesis/result by understanding the event circumstances. |

### NBNS - NetBIOS Name Services

| **Notes**                                                                                                                                                                       | **Wireshark Filter**             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| Global search.                                                                                                                                                                  | - `nbns`                         |
| "NBNS" options for grabbing the low-hanging fruits:<br><br>- **Queries:** Query details.<br>- Query details could contain **"name, Time to live (TTL) and IP address details"** | - `nbns.name contains "keyword"` |

---

### Kerberos

| **Notes**                                                                                                                                                                                                                                                                                                                                                                               | **Wireshark Filter**                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Global search.                                                                                                                                                                                                                                                                                                                                                                          | - `kerberos`                                                                                                       |
| User account search:<br><br>- **CNameString:** The username.<br><br>**Note:** Some packets could provide hostname information in this field. To avoid this confusion, filter the **"$"** value. The values end with **"$"** are hostnames, and the ones without it are user names.                                                                                                      | - `kerberos.CNameString contains "keyword"` <br>- `kerberos.CNameString and !(kerberos.CNameString contains "$" )` |
| "Kerberos" options for grabbing the low-hanging fruits:<br><br>- **pvno:** Protocol version.<br>- **realm:** Domain name for the generated ticket.  <br>    <br>- **sname:** Service and domain name for the generated ticket.<br>- **addresses:** Client IP address and NetBIOS name.  <br>    <br><br>**Note:** the "addresses" information is only available in request packets.<br> | - `kerberos.pvno == 5`<br><br>- `kerberos.realm contains ".org"` <br><br>- `kerberos.SNameString == "krbtg"`       |

---


### ICMP Tunneling
> *As it is a trusted network layer protocol, sometimes it is used for denial of service (DoS) attacks; also, adversaries use it in data exfiltration and C2 tunnelling activities...*

- ICMP protocols afford opportunities to carry extra data.
- Indicators
	- Large volumes of ICMP traffic
	- Anomalous ICMP packet sizes
		- *Custom packets can still be made which match the standard ICMP packet size of 64 bytes...*


| **Notes**                                                                                                                                                                | **Wireshark filters**      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------- |
| Global search                                                                                                                                                            | - `icmp`                   |
| "ICMP" options for grabbing the low-hanging fruits:<br><br>- Packet length.<br>- ICMP destination addresses.  <br>    <br>- Encapsulated protocol signs in ICMP payload. | - `data.len > 64 and icmp` |


---

### DNS Tunneling

- Indicators
	- Longer queries than typical ones
	- Crafted for subdomain addresses
		- These are actually encoded commands
			- `encoded-commands.malware.com`


| **Notes**                                                                                                                                                                                                                                                                                                                                                                                 | **Wireshark Filter**                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Global search                                                                                                                                                                                                                                                                                                                                                                             | - `dns`                                                              |
| "DNS" options for grabbing the low-hanging fruits:<br><br>- Query length.<br>- Anomalous and non-regular names in DNS addresses.<br>- Long DNS addresses with encoded subdomain addresses.<br>- Known patterns like dnscat and dns2tcp.<br>- Statistical analysis like the anomalous volume of DNS requests for a particular target.<br><br>**!mdns:** Disable local link device queries. | - `dns contains "dnscat"`<br><br>- `dns.qry.name.len > 15 and !mdns` |


