# Design-of-Local-Area-Network(Group_Project)
# University of Moratuwa Network Design Project

This project presents the **backbone network design** for the University of Moratuwa (UOM), along with a detailed **Local Area Network (LAN)** design for the **Department of Electronic and Telecommunication Engineering (ENTC)** building.

Both networks were **simulated using Cisco Packet Tracer and GNS3** following standard best practices and with consideration for future scalability, reliability, and maintainability.

---

## 📁 Project Folder Structure

```
/UOM_Network_Project/
│
├── Entc_network.pkt               # Cisco Packet Tracer file for ENTC LAN
├── LAN_Report.pdf                 # Final project report
├── README.md                      # Project summary and simulation guide
│
│
└── UNI_backbone                   # Cisco Packet Tracer file for UOM backbone
```

---


---

## 📌 Report Overview

### 1. Introduction

- The university consists of multiple buildings: academic departments, library, CITeS data center, etc.
- A long-term, cost-effective, scalable network backbone is required.

---

### 2. Internal Network of the ENTC Building

#### 2.1 LAN Features
- VLANs for staff, students, labs.
- Access switches connect to a distribution switch.
- Firewall and DHCP configuration included.

#### 2.2 ENTC LAN Topology
- Hierarchical model.
- Star topology with core-distro-access structure.

#### 2.3 ENTC Simulation
- Packet Tracer `.pkt` file: `ENTC_Network.pkt`.
- Successful ping and DHCP configuration.
- Wireless router with WPA2 authentication.

#### 2.4 Secure Wireless Access
- Wireless SSID: `UOM_ENTC_SECURE`
- WPA2-PSK implemented in the simulation.

---

### 3. Backbone Network Design

#### 3.1 Overview
- Connects ENTC, CITeS, Library, IT, Mechanical, Textile, Civil, Administration, Sumanadasa.

#### 3.2 Topology
- **Ring topology** at core using **Layer 3 switches (Catalyst 9300)**.
- **Star topology** from distribution to access.
- Redundancy via dual-homing links.

#### 3.3 Design Considerations
- Scalable up to 25 years.
- Fiber optic links (single-mode between buildings, multi-mode internally).
- Core switching at CITeS.
- Distribution switches at each building.

#### 3.4 Network Diagram
- See `Report.pdf` – includes full topology with bandwidth notations.

#### 3.5 Simulation Results
- Simulated using Cisco Packet Tracer.
- OSPF routing enabled across core.
- All nodes can reach each other via IPv4.

---

## 🧮 IPv4 Addressing Scheme

Each department/building has a unique subnet using `/22` or `/24`. Below is a sample:

### ENTC
| Port               | IP Address   | Subnet Mask     |
|--------------------|--------------|-----------------|
| Gi1/0/1            | 10.0.16.1    | 255.255.252.0    |
| Gi1/0/2            | 10.0.20.1    | 255.255.252.0    |
| Gi1/0/3            | 10.0.24.1    | 255.255.252.0    |
| Gi1/1/1            | 192.168.10.2 | 255.255.255.0    |
| Gi1/1/2            | 192.168.20.1 | 255.255.255.0    |

### Library
| Port               | IP Address   | Subnet Mask     |
|--------------------|--------------|-----------------|
| Gi1/0/1 – Gi1/0/3  | 10.0.64.1 – 10.0.72.1 | 255.255.252.0 |
| Gi1/1/1            | 192.168.30.1          | 255.255.255.0 |
| Gi1/1/2            | 192.168.20.2          | 255.255.255.0 |

### NOC (CITeS)
| Port               | IP Address   | Subnet Mask     |
|--------------------|--------------|-----------------|
| Gi1/0/1            | 10.100.0.2   | 255.255.255.0    |
| Gi1/1/1            | 192.168.10.1 | 255.255.255.0    |
| Gi1/1/2            | 192.168.100.1| 255.255.255.0    |
| Gi1/1/3            | 192.168.80.1 | 255.255.255.0    |

*(More tables included in the report)*

---

## ⚙️ Active & Passive Components

### Active Devices

- **Layer 3 Switches (Cisco Catalyst 9300)**
  - 24/48 Gigabit ports
  - 4 x 10GE uplinks
  - VLAN & OSPF support

- **Access Switches**
  - Cisco 2960 series
  - Used at endpoint floors/labs

- **Wireless Routers**
  - Dual-band
  - WPA2-enabled
  - DHCP and NAT support

### Passive Components

- Cat6a Ethernet cabling (internal)
- Single-mode fiber optic cabling (inter-building)
- Patch panels, sockets, 12U/42U network racks

---

## 🔧 How to Run Simulation

1. Open **Cisco Packet Tracer**.
2. Load the following files:
   - `Entc_network.pkt` – for ENTC LAN simulation
   - `UNI_backbone` – for backbone routing simulation
3. Check:
   - IP connectivity (`ping`)
   - OSPF convergence (`show ip route`)
   - VLANs and wireless SSID security
   - Inter-department communication

---

## 📌 Notes

- IPv6 not implemented in this version.
- Please refer to `LAN_Report.pdf` for diagrams, configurations, and explanations in detail.

---
