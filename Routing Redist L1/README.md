Overview
This EVE-NG lab simulates a large-scale enterprise network to demonstrate complex multi-protocol route redistribution. Consisting of 20 Cisco router nodes, the topology integrates   OSPF (Areas 0, 1, 2)  ,   EIGRP (AS 100)  , and   RIPv2  . The primary objective is to configure intra-domain routing, establish mutual redistribution at key boundary routers (ASBRs), and implement route filtering to prevent routing loops and suboptimal path selection across dual-homed boundaries. 

Configuration Sample: Mutual Redistribution (R7)

Below is a sample configuration for   R7  , acting as an Autonomous System Boundary Router (ASBR) mutually redistributing routes between   OSPF Area 1   and   EIGRP AS 100  .

! --- R7 OSPF Configuration ---
router ospf 10
 router-id 7.7.7.7
 network 6.0.0.0 0.0.0.255 area 1
 network 7.0.0.0 0.0.0.255 area 1
 network 12.0.0.0 0.0.0.255 area 1
 ! Redistribute EIGRP into OSPF
 redistribute eigrp 100 subnets metric-type 1
 
! --- R7 EIGRP Configuration ---
router eigrp 100
 network 16.0.0.0 0.0.0.255
 no auto-summary
 ! Redistribute OSPF into EIGRP (Bandwidth, Delay, Reliability, Load, MTU)
 redistribute ospf 10 metric 100000 10 255 1 1500