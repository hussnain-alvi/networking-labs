Router on a Stick Switching Lab

Overview
This repository contains the configuration files and topology details for a Router-on-a-Stick switching lab built in EVE-NG. The network design implements inter-VLAN routing using a single physical router interface configured with IEEE 802.1Q tagged subinterfaces, connected through a core and access switching hierarchy.

The simulated environment consists of the following core components:
 - Router3725: Acts as the layer 3 gateway, terminating 802.1Q VLAN tags and routing traffic between subnets.  
 - Core-Switch: Functions as the central distribution hub, passing trunked VLAN traffic down to the access layer.  
 - Switch1 & Switch2: Access switches segmenting traffic and connecting virtual PCs into specific VLAN

Sample: Router SubinterfacesBelow is the router configuration sample demonstrating 802.1Q encapsulation and gateway IP assignment for inter-VLAN routing:  

interface FastEthernet0/0
 no ip address
 no shutdown

interface FastEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0

interface FastEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.254 255.255.255.0

interface FastEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.254 255.255.255.0