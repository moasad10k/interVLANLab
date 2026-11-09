
# Cisco Inter-VLAN Routing

## 1. Project Overview

This project demonstrates inter-VLAN routing using a Cisco 2901 router and a switch in Cisco Packet Tracer.

The network is divided into two VLANs representing separate departments:

- **VLAN 2 – Management**
- **VLAN 3 – Finance**

Router-on-a-stick was implemented to enable communication between the two VLANs.

## 2. Network Topology

The network consists of one router, one switch, and four PCs. Each department has two PCs assigned to its respective VLAN.

![Network Topology](screenshots/topology.png)

## 3. IP Addressing

| Device | VLAN | IPv4 Address | Default Gateway |
|---|---|---|---|
| PC1 | 2 | 192.168.2.10 | 192.168.2.1 |
| PC2 | 2 | 192.168.2.11 | 192.168.2.1 |
| PC3 | 3 | 192.168.3.10 | 192.168.3.1 |
| PC4 | 3 | 192.168.3.11 | 192.168.3.1 |

**Subnet Mask:** 255.255.255.0 (/24)

## 4. Configuration & Implementation

### 4.1 VLAN Creation

Created and named the two VLANs on the switch:

- VLAN 2 – Management
- VLAN 3 – Finance

**VLAN Creation Configuration:**

![VLAN Creation](screenshots/vlan-creation.png)

### 4.2 PC Port Assignment

Assigned the switch access ports to their respective VLANs:

- Fa0/1–Fa0/2 → VLAN 2
- Fa0/3–Fa0/4 → VLAN 3

**PC Port Assignment Configuration:**

![PC Port Assignment](screenshots/port-assignment.png)

### 4.3 Initial Connectivity Testing

Tested communication between PCs in the same VLAN. Same-VLAN communication was successful, while communication between different VLANs was unsuccessful before inter-VLAN routing was configured.

**Same-VLAN Connectivity:**

![Same-VLAN Connectivity](screenshots/connectivity-same-vlan.png)

**Inter-VLAN Connectivity Before Routing:**

![Inter-VLAN Before Routing](screenshots/connectivity-inter-vlan-before.png)

### 4.4 Switch Trunk Configuration

Configured the switch port connected to the router as a trunk port to carry traffic from both VLANs.

**Switch Trunk Configuration:**

![Switch Configuration](screenshots/switch-configuration.png)

### 4.5 Router Interface Configuration

Enabled the router's physical GigabitEthernet interface using `no shutdown`.

**Router Interface Configuration:**

![Router Interface Configuration](screenshots/router-interface.png)

### 4.6 Router Subinterface Configuration

Configured router subinterfaces for each VLAN using 802.1Q encapsulation:

- **G0/0.2:** VLAN 2 – 192.168.2.1
- **G0/0.3:** VLAN 3 – 192.168.3.1

**Router Subinterface Configuration:**

![Router Configuration](screenshots/router-configuration.png)

### 4.7 Final Connectivity Testing

Tested communication between PCs in different VLANs. Successful communication confirmed that inter-VLAN routing was working.

**Inter-VLAN Connectivity After Routing:**

![Inter-VLAN After Routing](screenshots/connectivity-inter-vlan-after.png)

### 4.8 Configuration Verification

Verified the VLAN configuration using `show vlan brief`.

**VLAN Verification:**

![VLAN Brief](screenshots/vlan-brief.png)

Verified router interface and subinterface status using `show ip interface brief`.

**Router Interface Verification:**

![Interface Brief](screenshots/interface-brief.png)

## 5. Troubleshooting

### 5.1 Scenario 1: Incorrect Default Gateway

**Problem:** PC1 could communicate with another PC in the same VLAN but could not communicate with a PC in a different VLAN.

**Diagnosis:** The default gateway configured on PC1 was incorrect.

**Cause:** PC1 was configured with `192.168.2.254` instead of `192.168.2.1`.

**Solution:** Corrected PC1's default gateway to `192.168.2.1`.

**Verification:** Successfully tested communication within and between VLANs after correcting the gateway.

**Before Correction:**

![Incorrect Default Gateway](screenshots/gateway-troubleshooting-before.png)

**After Correction:**

![Correct Default Gateway](screenshots/gateway-troubleshooting-after.png)

### 5.2 Scenario 2: Incorrect VLAN Assignment

**Status:** PENDING

**Problem:** To be documented after testing.

**Diagnosis:** Pending.

**Solution:** Pending.

**Verification:** Pending.

**Before Correction:**

![Incorrect VLAN Assignment](screenshots/vlan-assignment-before.png)

**After Correction:**


![Correct VLAN Assignment](screenshots/vlan-assignment-after.png)
