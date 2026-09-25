# Design, Implementation, and Troubleshooting of a Hierarchical Enterprise Network Infrastructure

## Project Overview

This project presents the design and implementation of a secure, scalable, hierarchical enterprise network for a four-story banking and insurance company establishing operations in Nairobi, Kenya. The network was modeled and simulated using **Cisco Packet Tracer**, following the **Cisco Three-Layer Hierarchical Network Design** model (Core, Distribution, and Access layers).

The project demonstrates end-to-end enterprise networking concepts including dynamic routing, VLAN segmentation, dynamic IP addressing, wireless connectivity, and secure remote administration.

---

## Network Requirements

- Four-story building, each floor hosting multiple departments
- Each department isolated in its own VLAN and subnet
- Wireless connectivity available for every department
- Dynamic IPv4 addressing for all host devices via centralized DHCP servers
- Centralized HTTP and Email servers
- Secure remote management via SSH
- Port-level security on all access switches
- Full inter-department (inter-VLAN) communication

---

## Network Topology

The design follows a hierarchical structure:

- **Access Layer** — Layer 2 switches per department, providing end-user connectivity (wired and wireless)
- **Distribution Layer** — Multilayer switches per floor, handling inter-VLAN routing (Switch Virtual Interfaces)
- **Core Layer** — Redundant routers interconnecting all four floors and the server room, running dynamic routing

Each floor connects to the core via dual uplinks for redundancy.

---

## Technologies & Concepts Implemented

| Category | Technology / Feature |
|---|---|
| Network Modeling | Cisco Packet Tracer |
| Design Methodology | Hierarchical (Core–Distribution–Access) Network Design |
| Routing Protocol | OSPF (Open Shortest Path First) |
| VLAN Segmentation | Per-department VLANs and subnets |
| Inter-VLAN Routing | Switch Virtual Interfaces (SVI) on multilayer switches |
| IP Addressing | Custom subnetting from a single base network |
| Dynamic Addressing | Centralized DHCP server(s) with IP helper-address relay |
| Servers | Dedicated HTTP and Email servers |
| Remote Management | SSH with local authentication, encrypted passwords |
| Port Security | Sticky MAC learning, violation mode: shutdown |
| Wireless | Departmental Wireless LAN via Access Points |
| Device Hardening | Hostnames, banners, disabled domain lookup, encrypted passwords |

---

## IP Addressing Scheme

The network uses a single base network address, subnetted according to the number of hosts required per department. Each department/VLAN was assigned:

- A unique subnet and subnet mask (VLSM-based)
- A defined usable IP address range
- A broadcast address
- A default gateway (multilayer switch SVI)

DHCP pools were configured on the centralized DHCP server(s) to match each department's subnet, gateway, and DNS settings.

---

## VLAN Design

Each department across the four floors was assigned a distinct VLAN ID and corresponding subnet, ensuring full Layer 2 isolation between departments while allowing controlled Layer 3 communication via inter-VLAN routing.

---

## Key Configuration Areas

- Basic device configuration (hostnames, console/enable passwords, banners, password encryption, disabled domain lookup)
- VLAN creation and port assignment on all access switches
- Trunk configuration between access and distribution switches
- SVI (Switch Virtual Interface) configuration for inter-VLAN routing
- OSPF configuration across all routing devices for full network reachability
- DHCP server configuration with per-department pools and IP helper-addresses
- SSH configuration (local user database, RSA key generation, VTY line security)
- Port security configuration (sticky MAC addresses, maximum address limits, shutdown violation mode)
- Wireless Access Point configuration per department

---

## Verification & Testing

The completed network was tested and verified for:

- End-to-end connectivity between all departments across all floors
- Dynamic IP address allocation to wired and wireless hosts
- OSPF route propagation across the entire network
- Secure remote SSH access to network devices
- HTTP and Email server accessibility from client devices
- Wireless client connectivity per department
- Port-security enforcement on access ports

---

## Screenshots

**Full Network Topology**

![Network Topology](screenshots/topology.png)

**OSPF Route Table Verification**

![OSPF Routes](screenshots/ospf-routes.png)

**DHCP Dynamic IP Allocation (Client Side)**

![DHCP Client](screenshots/dhcp-client.png)

**Secure SSH Remote Login**

![SSH Login](screenshots/ssh-login.png)

**HTTP Server Access**

![HTTP Server](screenshots/http-server.png)

---

## Repository Contents

- Packet Tracer topology file (`.pkt`)
- `/screenshots` — network topology and verification screenshots
- IP addressing / subnetting plan
- Device configuration references

---

## Tools Used

- Cisco Packet Tracer (network simulation and implementation)
- Draw.io / Visio (logical topology visualization)

---

## Notes

This project was developed as an academic exercise in enterprise network design, applying real-world hierarchical networking principles to a simulated banking sector use case.
