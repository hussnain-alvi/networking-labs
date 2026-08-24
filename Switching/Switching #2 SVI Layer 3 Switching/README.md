Multilayer Switching & SVI Lab 

Overview
This repository contains the configuration files and topology details for a **Multilayer SVI (Switched Virtual Interface) Layer 3 Switching** lab built in EVE-NG.

Configuration Sample: Core-Switch SVI Setup
Below is the core configuration demonstrating Switched Virtual Interfaces (SVIs) configured on the `Core-Switch` to route traffic between VLANs 10, 20, and 30[cite: 5]:

! --- Core-Switch SVI Configuration ---
interface Vlan10
 no shutdown
 ip address 192.168.10.254 255.255.255.0

interface Vlan20
 no shutdown
 ip address 192.168.20.254 255.255.255.0

interface Vlan30
 no shutdown
 ip address 192.168.30.254 255.255.255.0

! --- Trunking to Access Switches ---
interface Ethernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30

interface Ethernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30