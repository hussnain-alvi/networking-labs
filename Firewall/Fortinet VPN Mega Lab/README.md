Enterprise Multi-Site Architecture: Fortinet VPN Mega Lab

Lab Overview
This repository contains the EVE-NG topology for a large-scale, multi-site enterprise network named "Firewall Mega Lab 1"[cite: 1]. The primary objective of this environment is to demonstrate secure inter-site communication using Fortinet firewalls, alongside a fully realized hierarchical switching model and a functional Demilitarized Zone (DMZ). 

Infrastructure Components
This mega lab utilizes a diverse set of virtualized network and server instances[cite: 1]:
- Edge Security: 2x Fortinet FortiGate (FGT v6.4) firewalls acting as the gateways for the LHR and KHI sites[cite: 1].
- Routing & Switching: Cisco IOL (L2 and L3) images forming the Core, Distribution, and Access layers[cite: 1]. 
- DMZ Servers: Windows Server 2016 (DNS) and CentOS 7 Linux instances (SAMBA, FTP)[cite: 1].
- Endpoints: Over 20 Virtual PCs (VPCs) and Windows client machines distributed across the access switches[cite: 1].

Network Architecture
The topology simulates a real-world corporate WAN setup with the following segments:
- Site-to-Site VPN: The Lahore (FW_LHR) and Karachi (FW_KHI) firewalls are separated by a simulated ISP router/bridge, requiring IPsec VPN tunneling for secure internal traffic routing. 
- Dedicated DMZ: A segregated switch off the primary firewall hosts public-facing or essential core services (DNS, FTP, SAMBA)[cite: 1].
- Hierarchical LAN: The internal network features redundant core switching (Core_Switch1 and Core_Switch2) distributing traffic down to 11 individual access switches[cite: 1].