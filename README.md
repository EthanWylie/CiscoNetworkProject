# Small Business Network Infrastructure

A Cisco Packet Tracer personal networking project demonstrating introductory Cisco networking skills.

## Project Overview

Designed and configured a small-business network using Cisco Packet Tracer. The network separates devices and services using VLANs and provides DHCP, inter-VLAN routing, SSH remote management, DNS, and an internal web server.

## Network Devices

* **R1** — Cisco 1941 router
* **SW1** — Cisco 2960-24TT switch
* **SERVER1** — Web and DNS server
* **PC-IT**
* **PC-EMPLOYEE**
* **PC-GUEST**
* **PC-MANAGEMENT**

## VLANs

| VLAN | Name       | Network      | Gateway   |
| ---- | ---------- | ------------ | --------- |
| 10   | IT         | 10.0.10.0/24 | 10.0.10.1 |
| 20   | Employee   | 10.0.20.0/24 | 10.0.20.1 |
| 30   | Server     | 10.0.30.0/24 | 10.0.30.1 |
| 40   | Guest      | 10.0.40.0/24 | 10.0.40.1 |
| 50   | Management | 10.0.50.0/24 | 10.0.50.1 |

## Switch Ports

| Port   | VLAN  | Device        |
| ------ | ----- | ------------- |
| Fa0/1  | 10    | PC-IT         |
| Fa0/2  | 20    | PC-EMPLOYEE   |
| Fa0/3  | 40    | PC-GUEST      |
| Fa0/4  | 50    | PC-MANAGEMENT |
| Fa0/10 | 30    | SERVER1       |
| Fa0/24 | Trunk | R1 G0/0       |

## Routing

R1 uses router-on-a-stick configuration to provide communication between VLANs.

* G0/0.10 → 10.0.10.1
* G0/0.20 → 10.0.20.1
* G0/0.30 → 10.0.30.1
* G0/0.40 → 10.0.40.1
* G0/0.50 → 10.0.50.1

## DHCP

R1 provides DHCP to the client VLANs.

* VLAN 10 — IT
* VLAN 20 — Employee
* VLAN 40 — Guest
* VLAN 50 — Management

The first 20 addresses in each client subnet are excluded from DHCP.

## Server

SERVER0 uses:

```text
IP Address: 10.0.30.10
Subnet Mask: 255.255.255.0
Default Gateway: 10.0.30.1
DNS Server: 10.0.30.10
```

HTTP and DNS services are enabled.

## Internal Website

The Packet Tracer network includes an internal website:

```text
http://www.wylie.com
```

DNS maps:

```text
www.wylie.com → 10.0.30.10
```

This is a simulated/local Packet Tracer domain and is not an Internet website.

## SSH Management

SW1 uses VLAN 50 as its management network.

```text
SW1: 10.0.50.2
R1 Gateway: 10.0.50.1
```

SSH was configured for remote management and VTY access was restricted to SSH instead of Telnet.

Example:

```text
ssh -l admin 10.0.50.2
```

## Verification

Useful Cisco IOS commands:

```text
show vlan brief
show ip interface brief
show ip dhcp binding
show running-config
```

## Skills Demonstrated

* IPv4 addressing
* Basic subnetting
* VLAN configuration
* Access ports
* Trunking
* Router-on-a-stick
* Inter-VLAN routing
* DHCP
* Basic Cisco IOS
* SSH remote management
* DNS
* HTTP
* Basic network troubleshooting
* Network verification

## Project Files

* `CiscoNetworkProject.pkt` — Cisco Packet Tracer network
* `NetworkIPAddressing.xlsx` — IP and VLAN addressing plan
* `NetworkTopology.png` — Image of network topology
* `CiscoSmallBusinessNetwork.pdf` — Detailed configuration documentation
* `README.md` — Project overview and documentation
