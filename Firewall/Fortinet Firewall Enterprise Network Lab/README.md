Fortinet Firewall Enterprise Network Lab

Overview
This repository and topology demonstrate an enterprise-grade network architecture secured and managed by a centralized Fortinet Firewall acting as the perimeter defense and inter-subnet gateway.

The design implements strict network segmentation, separating standard user departments from sensitive server infrastructure while managing external internet access.

Key Architectural Components
Perimeter Security & Gateway (LHR_FW):
Connects the internal enterprise network to the external ISP cloud.
Enforces security policies, access control lists, and routing between internal VLANs, the DMZ, and the internet.

Core Routing (CORE-SW):
Acts as the central switching hub interfacing directly with the firewall's internal port.
Distributes traffic across multiple access switches (AS-1, AS-2, AS-3) to support user workstations.

Demilitarized Zone / Server Segment (VLAN 30):
Isolated behind the firewall via a dedicated DMZ_Switch (192.168.30.0/24).
Hosts critical backend infrastructure, including Active Directory (AD_SRV), Web servers (WEB_SRV), and file/Linux servers (192.168.30.11 through 192.168.30.13).

User Access Layers:
VLAN 10 (192.168.10.0/24): Dedicated segment for IT department endpoints and client PCs (VPC1 to VPC12).
VLAN 20 (192.168.20.0/24): Dedicated segment for HR department endpoints and workstations.