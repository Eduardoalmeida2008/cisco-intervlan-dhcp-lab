# Networking_Lab_VLAN_DHCP
Hands-on lab simulating VLANs, DHCP configuration, inter-VLAN routing, and connectivity tests using Cisco routers and switches.

# Networking Lab: VLANs and DHCP

This lab simulates a small corporate network with multiple VLANs, DHCP configuration, inter-VLAN routing, and connectivity tests using Cisco devices.

---

## Lab Objectives

1. Configure VLANs on multiple switches.
2. Configure DHCP pools on routers for each VLAN.
3. Configure subinterfaces on routers for inter-VLAN routing.
4. Test connectivity between VLANs using ping.
5. Document the lab with screenshots for each step.

---

## Lab Topology

- 2 Routers: R1, R2
- 3 Access Switches: SW1, SW2, SW3
- VLANs:
  - SW1: VLAN10, VLAN20
  - SW2: VLAN30, VLAN40
  - SW3: VLAN50
- PCs: 3 per VLAN
- Trunk links configured between switches and routers
- Point-to-point link between R1 and R2

![Topology](images/Topology.png)

---

## Screenshots and Documentation

### DHCP Configuration
- All VLAN DHCP pools configured on routers
- Screenshot: `images/DHCP_VLANs.png`

### Router Subinterfaces
- All subinterfaces with dot1Q encapsulation
- Screenshot: `images/Subinterfaces_R1.png`

### Router IP Interface Brief
- Show summary of all interfaces and subinterfaces
- Screenshot: `images/IP_Interface_Brief_R1.png`

### Running Configurations
- R1: `images/Show_Running_Config_R1.png`
- SW1: `images/Show_Running_Config_SW1.png`
- SW2: `images/Show_Running_Config_SW2.png`
- SW3: `images/Show_Running_Config_SW3.png`

### Connectivity Tests
- Ping tests between VLANs from VLAN10:
  - `images/Ping_VLAN10_to_VLAN20.png`
  - `images/Ping_VLAN10_to_VLAN30.png`
  - `images/Ping_VLAN10_to_VLAN40.png`
  - `images/Ping_VLAN10_to_VLAN50.png`

---

## Notes
- All configurations use Cisco IOS commands.
- VLAN and DHCP settings are documented in each screenshot.
- Subinterfaces are used for inter-VLAN routing.
- Trunks configured to carry multiple VLANs between switches and routers.
- IP addressing uses private ranges and /24 subnets for VLANs, /30 for point-to-point links.

