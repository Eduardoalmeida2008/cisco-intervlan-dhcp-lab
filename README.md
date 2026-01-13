# Enterprise Network Infrastructure: Inter-VLAN Routing & DHCP Services

## 📌 Project Overview
This project demonstrates the implementation of a segmented enterprise network using Cisco Packet Tracer. The core objective was to design a scalable architecture that isolates departments into distinct VLANs while maintaining controlled communication through a Router-on-a-Stick topology and automated IP addressing via DHCP.

## 🚀 Technical Features
* **VLAN Segmentation:** Isolation of 5 different departments to improve security and network performance.
* **Inter-VLAN Routing:** Implementation of 802.1Q encapsulation using subinterfaces on a Cisco Router.
* **Dynamic Addressing:** Configuration of multiple DHCP pools directly on the router to automate IP assignment for each VLAN.
* **L3 Connectivity:** Static routing between different network segments to ensure end-to-end reachability.

## 🗺️ Network Topology
The network consists of:
- **1 Cisco Router (2911):** Acting as the Default Gateway and DHCP Server.
- **3 Cisco Switches (2960):** Handling access layer connectivity and VLAN tagging.
- **End Devices:** Multiple PCs simulating different departments (Sales, HR, IT, etc.).

## 📊 IP Addressing Plan
| VLAN | Department | Subnet | Gateway |
| :--- | :--- | :--- | :--- |
| 10 | Sales | 192.168.10.0/24 | 192.168.10.1 |
| 20 | HR | 192.168.20.0/24 | 192.168.20.1 |
| 30 | IT | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Management | 192.168.40.0/24 | 192.168.40.1 |
| 50 | Servers | 192.168.50.0/24 | 192.168.50.1 |

## ⚙️ Configuration Highlights

### 1. Router-on-a-Stick (Subinterfaces)
```bash
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
!
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
````

2. DHCP Pool Configuration
   
ip dhcp pool VLAN_10_SALES
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8

 🧪 Verification & Troubleshooting
The following commands were used to verify the infrastructure:

show ip interface brief: To verify subinterface status.

show vlan brief: To confirm VLAN assignments on switches.

show ip route: To validate the routing table and static routes.

ICMP Connectivity: Successful pings between all VLANs were achieved, confirming the Router-on-a-Stick functionality.

📸 Lab Screenshots
(Insert your best screenshots here, such as the topology diagram and the successful ping tests)

Developed by [Eduardo] Network Engineering Student | CCNA Candidate
