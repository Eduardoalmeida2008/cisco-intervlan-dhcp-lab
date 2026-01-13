# Enterprise Network: Inter-VLAN Routing & Multi-Pool DHCP Implementation

## 📌 Overview
This repository documents a complete Layer 3 network infrastructure lab. The project focuses on segmenting a corporate network into functional VLANs, providing automated IP addressing via a centralized DHCP server on a Cisco Router, and establishing connectivity between different network segments using Router-on-a-Stick.

## 🚀 Key Implementation Details
* **Router-on-a-Stick (Dot1Q):** Subinterface configuration on `Gig0/0` to route traffic between 5 distinct VLANs.
* **Centralized DHCP Server:** Multiple pools configured on the R1 router to serve IPs dynamically based on the originating VLAN.
* **Static Routing:** Established link between R1 and R2 via the `192.168.100.0/30` network to simulate connectivity to a remote site or server farm (VLAN 50).
* **VLAN Trunking:** Configured 802.1Q trunk links between switches to carry tagged traffic across the topology.

## 📊 Technical Addressing Plan (Based on Lab Data)
| Interface / Subinterface | VLAN | Network | Description |
| :--- | :--- | :--- | :--- |
| Gig0/0.10 | 10 | 192.168.10.0/24 | Sales |
| Gig0/0.20 | 20 | 192.168.20.0/24 | HR |
| Gig0/0.30 | 30 | 192.168.30.0/24 | Finance |
| Gig0/0.40 | 40 | 192.168.40.0/24 | IT / Management |
| Gig0/1 (R2 Link) | - | 192.168.100.0/30 | Point-to-Point Link |
| R2 Gig0/0 | 50 | 192.168.50.0/24 | Servers |

## ⚙️ Configuration Snippets (Verified)

### Subinterface Configuration (R1)
```
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
!
interface GigabitEthernet0/0.40
 encapsulation dot1Q 40
 ip address 192.168.40.1 255.255.255.0
````

DHCP Pool Setup (R1)
```
ip dhcp pool VLAN_10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
!
ip dhcp pool VLAN_40
 network 192.168.40.0 255.255.255.0
 default-router 192.168.40.1
````
Inter-Router Static Route
````
! On R1: Reaching the Server Network (VLAN 50) via R2
ip route 192.168.50.0 255.255.255.0 192.168.100.2
````
🧪 Testing and Validation
```
DHCP Acknowledgement: Verified on PCs (e.g., PC-VLAN40 received 192.168.40.2 via DHCP).

Routing Table: show ip route confirms the existence of connected subnets and the static route to the remote segment.

Connectivity: Successful ICMP echo requests (pings) between PC-VLAN10 and Server-VLAN50, validating the entire path.
```
📸 Evidence
```
(Upload your screenshots here, specifically the 'show ip interface brief' and the successful ping tests you've captured)
````
