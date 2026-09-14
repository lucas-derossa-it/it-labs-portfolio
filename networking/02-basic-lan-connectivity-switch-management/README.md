# Basic LAN Connectivity and Switch Management

Hands-on Cisco Packet Tracer lab focused on building, securing, and validating a small Layer 2 LAN using two Cisco switches and two end devices.

## Scenario

The lab uses two Cisco 2960 switches connected to each other, with one PC connected to each switch. All devices operate in the same IPv4 subnet, `192.168.1.0/24`, so no router is required for local communication.

## Addressing Plan

| Device | Interface | IPv4 Address | Subnet Mask |
|---|---|---:|---:|
| PC1 | FastEthernet0 | `192.168.1.1` | `255.255.255.0` |
| PC2 | FastEthernet0 | `192.168.1.2` | `255.255.255.0` |
| S1 | VLAN 1 SVI | `192.168.1.253` | `255.255.255.0` |
| S2 | VLAN 1 SVI | `192.168.1.254` | `255.255.255.0` |

## What I Configured

- Assigned hostnames to both switches.
- Configured console access protection and privileged EXEC access using an enable secret.
- Added MOTD security banners.
- Configured management IP addresses on the VLAN 1 SVIs.
- Configured static IPv4 addressing on both PCs.
- Saved the running configuration to NVRAM with `copy running-config startup-config`.
- Verified switch interface status with `show ip interface brief`.
- Tested end-to-end connectivity using ICMP `ping` from both PCs.

## Troubleshooting Performed

During verification, I identified an unintended management IP configured on VLAN 2 of S2. I removed the IP address, administratively shut down the unused SVI, rechecked the interface status, and then saved the corrected configuration to NVRAM.

Initial ping attempts to some devices showed one dropped packet while address resolution completed. Repeating the tests produced successful connectivity with `0%` packet loss.

## Validation Results

- Packet Tracer assessment score: **88/88**
- Assessment items completed: **22/22**
- Final PC-to-PC connectivity: **Successful**
- Final PC-to-switch management connectivity: **Successful**
- Final repeated ping tests: **0% packet loss**

## Skills Demonstrated

Cisco IOS CLI, Layer 2 switching, IPv4 addressing, switch management interfaces, basic switch security, configuration persistence in NVRAM, ICMP testing, ARP awareness, and structured troubleshooting.

## Evidence

Supporting Packet Tracer file and screenshots are stored in the `evidence/` and `packet-tracer/` folders for this lab.

> Lab environment: Cisco Packet Tracer. Credentials used in this exercise are training-only values and are not representative of production password practices.
