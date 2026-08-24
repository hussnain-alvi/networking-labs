Enterprise Multilayer Switching Lab (SVI Architecture)

Overview
This package contains the complete EVE-NG topology and configuration files for an enterprise-grade Multilayer Switched Virtual Interface (SVI) network. It demonstrates robust inter-VLAN routing using a centralized Core_switch acting as the default gateway across multiple interconnected access switches and a dedicated server segment.

Network Topology & Components
 -Core Layer: Core_switch (Cisco IOL Layer 3 Switch) configured with SVIs for VLANs 10, 20, 30, 40, and 50.
 -Access Layer: Switch1, Switch2, Switch3, and Switch4 interconnecting virtual client PCs (VPC1 through VPC16) via 802.1Q trunking and access ports.
 -Services Layer: Switch5 connected to Winserver (Windows Server 2016) residing on VLAN 50.

Core Switch SVI Configuration Sample

! --- Core-Switch SVI Setup ---
interface Vlan10
 description Client Segment VLAN 10
 ip address 192.168.10.254 255.255.255.0
 no shutdown

interface Vlan50
 description Server Segment VLAN 50
 ip address 192.168.50.254 255.255.255.0
 no shutdown

! --- Trunking to Access Switches ---
interface Ethernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk