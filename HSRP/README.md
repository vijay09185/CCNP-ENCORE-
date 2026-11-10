
# HSRP - Gateway Redundancy Lab

## 1. Project Overview

This lab demonstrates Hot Standby Router Protocol (HSRP) using two Cisco routers (GW1 and GW2), one access switch and four PCs.

The purpose of this lab is to provide gateway redundancy using a shared virtual IP address.

If the active gateway fails, the standby gateway takes over the virtual gateway role, allowing PCs to continue using the same default gateway.

## 2. Lab Objectives

- Understand HSRP operation.
- Configure two gateways in an HSRP group.
- Configure a shared virtual IP address.
- Understand Active and Standby router roles.
- Configure PCs to use the HSRP virtual IP.
- Test gateway failover.
- Verify HSRP operation using Cisco IOS commands.

## 3. Network Devices

- GW1 - First gateway router.
- GW2 - Second gateway router.
- ASW - Access switch.
- PC0, PC1, PC2 and PC3 - End devices.

## 4. IP Addressing Table

### Gateway Configuration

| Device | Interface | IP Address |
|---|---|---|
| GW1 | Fa0/0 | 192.168.1.1 |
| GW2 | Fa0/0 | 192.168.1.2 |
| HSRP | Virtual IP | 192.168.1.3 |

Subnet Mask: 255.255.255.0

### PC Configuration

| Device | IP Address | Default Gateway |
|---|---|---|
| PC0 | 192.168.1.10 | 192.168.1.3 |
| PC1 | 192.168.1.20 | 192.168.1.3 |
| PC2 | 192.168.1.30 | 192.168.1.3 |
| PC3 | 192.168.1.40 | 192.168.1.3 |

## 5. HSRP Configuration

- HSRP Group: 1
- Virtual IP: 192.168.1.3
- GW1: Standby Gateway
- GW2: Active Gateway
- Default HSRP priority: 100 on both routers.
- GW2 wins the priority tie because it has the higher interface IP address.

## 6. Loopback Configuration

GW2 has an additional Loopback0 interface:

- Interface: Loopback0
- IP Address: 8.8.8.8
- Subnet Mask: 255.255.255.255

This provides an additional destination for routing and connectivity practice.

## 7. Verification Commands

Run these commands on both routers:

```cisco
show standby
show standby brief
show ip interface brief
show running-config
```

## 8. Testing Procedure

### Test 1 - Normal Connectivity

1. Ping 192.168.1.3 from the PCs.
2. Verify that GW2 is Active.
3. Verify that GW1 is Standby.
4. Check HSRP status using `show standby brief`.

### Test 2 - Gateway Failover

1. Verify the current Active and Standby roles.
2. Shut down the active gateway's LAN interface on GW2.
3. Check the HSRP status on GW1.
4. GW1 should become Active.
5. Test connectivity from the PCs using the same virtual IP.

### Test 3 - Gateway Recovery

1. Restore GW2's interface.
2. Verify the HSRP roles again.
3. Observe whether the original Active router resumes its role according to the configured preemption settings.

## 9. Expected Results

- All PCs use 192.168.1.3 as their default gateway.
- GW2 initially operates as Active.
- GW1 initially operates as Standby.
- GW1 takes over if GW2 becomes unavailable.
- The PCs do not need a default gateway change during failover.

## 10. Technologies Used

- Cisco Packet Tracer
- HSRP
- Gateway Redundancy
- Virtual IP Address
- Active/Standby Mechanism
- Loopback Interface
- Cisco IOS Verification Commands

## 11. Project Files

- HSRP-Lab.pkt - Packet Tracer topology.
- README.md - Lab documentation.
- configuration.txt - Device configuration commands.

---

**Project:** CCNP Enterprise Networking Lab Practice  
**Topic:** HSRP Gateway Redundancy
