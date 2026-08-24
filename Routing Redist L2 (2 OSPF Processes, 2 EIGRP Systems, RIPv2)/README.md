Enterprise Route Redistribution Lab(18 Routers- 2 OSPF Processes, 2 EIGRP Autonomous Systems, RIPv2)

Overview
This repository contains the topology files and configurations for an 18-node advanced route redistribution lab built in EVE-NG. The network architecture is segmented into multiple distinct routing domains, utilizing OSPF (Processes 20 and 100), EIGRP (Autonomous Systems 119 and 200), and RIPv2. The core objective of this lab is to establish intra-domain routing and configure mutual route redistribution at critical boundary nodes to achieve full end-to-end network reachability without introducing routing loops.

! --- R9 Interface Configuration (Reference) ---
! Interface facing R8 (OSPF)
interface Ethernet0/1
 ip address 8.8.8.1 255.0.0.0
 no shutdown

! Interface facing R10 (RIPv2)
interface Ethernet0/0
 ip address 9.9.9.1 255.0.0.0
 no shutdown

! --- R9 OSPF Configuration ---
router ospf 100
 router-id 9.9.9.9
 network 8.0.0.0 0.255.255.255 area 2
 ! Redistribute RIP routes into OSPF
 redistribute rip subnets

! --- R9 RIP Configuration ---
router rip
 version 2
 network 9.0.0.0
 no auto-summary
 ! Redistribute OSPF routes into RIP with a seed metric
 redistribute ospf 100 metric 2