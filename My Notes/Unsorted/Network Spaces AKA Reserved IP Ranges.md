# Network Spaces AKA Reserved IP Ranges

## Private Addresses
### IPv4
→ See [Wikipedia - Private IPv4 Addresses](https://en.wikipedia.org/wiki/Private_network#Private_IPv4_addresses)

| RFC 1918 name | IP address range              | Number of addresses | Largest [CIDR](https://en.wikipedia.org/wiki/CIDR "CIDR") block (subnet mask) | Host ID size | Mask bits | _[Classful](https://en.wikipedia.org/wiki/Classful "Classful")_ description |
| ------------- | ----------------------------- | ------------------- | ----------------------------------------------------------------------------- | ------------ | --------- | --------------------------------------------------------------------------- |
| 24-bit block  | 10.0.0.0 – 10.255.255.255     | 16777216            | 10.0.0.0/8 (255.0.0.0)                                                        | 24 bits      | 8 bits    | single class A network                                                      |
| 20-bit block  | 172.16.0.0 – 172.31.255.255   | 1048576             | 172.16.0.0/12 (255.240.0.0)                                                   | 20 bits      | 12 bits   | 16 contiguous class B networks                                              |
| 16-bit block  | 192.168.0.0 – 192.168.255.255 | 65536               | 192.168.0.0/16 (255.255.0.0)                                                  | 16 bits      | 16 bits   | 256 contiguous class C networks                                             |

### IPv6
→ See [Wikipedia - Private IPv6 Addresses](https://en.wikipedia.org/wiki/Private_network#Private_IPv6_addresses)

## Other Addresses & Ranges

### Link-local
> *The validity of link-local addresses is limited to a single link; e.g. to all computers connected to a switch, or to one wireless network. Hosts on different sides of a network bridge are also on the same link, whereas hosts on different sides of a network router are on different links.*

See → [Wikipedia - Link-Local Addresses](https://en.wikipedia.org/wiki/Private_network#Link-local_addresses)

- Covers IPv4, IPv6, and the loopback interface(s) for each.
- Loopback Interfaces
	- IPv4 → The entire class A block of `127.0.0.0/8`
	- IPv6 → `::1`


