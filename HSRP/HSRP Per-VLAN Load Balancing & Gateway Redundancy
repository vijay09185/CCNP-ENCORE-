# HSRP Per-VLAN Load Balancing & Gateway Redundancy

## 1. Project Overview

This project demonstrates HSRP (Hot Standby Router Protocol) with Per-VLAN Load Balancing using two Cisco gateways.

The network is designed to distribute gateway traffic across two gateways while maintaining redundancy.

GW1 acts as the preferred Active Gateway for VLAN 10 and VLAN 20, while GW2 acts as the preferred Active Gateway for VLAN 30 and VLAN 40.

If one gateway fails, the other gateway takes over its responsibilities.

## 2. Lab Objectives

- Configure multiple VLANs.
- Configure 802.1Q trunk links.
- Configure HSRP on two gateways.
- Implement Per-VLAN Gateway Load Balancing.
- Configure Active and Standby gateway roles.
- Implement gateway redundancy.
- Test gateway failure and recovery.
- Configure connectivity towards the ISP router.
- Verify inter-VLAN communication.

## 3. Network Topology

The topology consists of:

- GW1 – First gateway.
- GW2 – Second gateway.
- Access Switch – Connects gateways and end devices.
- Four PCs – Connected to separate VLANs.
- ISP Router – Provides upstream network connectivity.

Both gateways are connected to the access switch using trunk links.

## 4. VLAN Design

| VLAN | Preferred Active Gateway | Backup Gateway |
|---|---|---|
| VLAN 10 | GW1 | GW2 |
| VLAN 20 | GW1 | GW2 |
| VLAN 30 | GW2 | GW1 |
| VLAN 40 | GW2 | GW1 |

## 5. HSRP Design

HSRP is configured independently for each VLAN.

- GW1 has higher HSRP priority for VLAN 10 and VLAN 20.
- GW2 has higher HSRP priority for VLAN 30 and VLAN 40.
- The other gateway remains in Standby state for each VLAN.
- HSRP preemption is used on the preferred gateways where configured.
- Each VLAN uses its own virtual IP as its default gateway.

## 6. Network Functionality

The following functionalities are implemented:

### Per-VLAN Load Balancing
Traffic is distributed between GW1 and GW2 based on the VLAN's preferred Active Gateway.

### Gateway Redundancy
Each gateway provides backup for the other gateway.

### Inter-VLAN Routing
Devices belonging to different VLANs can communicate through the gateways.

### ISP Connectivity
Internal network devices can reach the ISP router through the configured gateway routing.

### Gateway Failover
If an Active Gateway fails, the Standby Gateway takes over the virtual gateway role.

## 7. Verification Commands

### Gateway Verification

```cisco
show standby brief
show standby
show ip interface brief
show ip route
show running-config
```

### Switch Verification

```cisco
show vlan brief
show interfaces trunk
show mac address-table
```

## 8. Testing & Results

| Test Case | Result |
|---|---|
| HSRP Active/Standby election | Passed |
| GW1 gateway failover | Passed |
| GW2 gateway failover | Passed |
| Per-VLAN load balancing | Passed |
| Inter-VLAN communication | Passed |
| ISP router connectivity | Passed |

## 9. Technologies Used

- Cisco Packet Tracer
- HSRP
- VLAN
- IEEE 802.1Q Trunking
- Inter-VLAN Routing
- Gateway Redundancy
- Per-VLAN Load Sharing
- Static Routing / Default Routing (as configured)

## 10. Project Files

- `HSRP-Load-Balancing.pkt` – Packet Tracer topology.
- `README.md` – Project documentation.
- `configuration.txt` – Device configurations.

## 11. Learning Outcome

This lab demonstrates how enterprise networks can distribute gateway responsibilities across multiple Layer 3 gateways while maintaining network availability through HSRP.

It also provides practical experience in VLAN configuration, trunking, routing, redundancy, failover testing and network troubleshooting.

---

**Project:** CCNP Enterprise Networking Labs  
**Topic:** HSRP Per-VLAN Load Balancing  
**Platform:** Cisco Packet Tracer
