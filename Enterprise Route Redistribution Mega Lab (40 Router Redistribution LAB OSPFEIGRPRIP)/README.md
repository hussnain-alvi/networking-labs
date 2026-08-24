Enterprise Route Redistribution Mega Lab (40 Router Redistribution LAB: OSPF/EIGRP/RIP)

Overview
This repository contains the topology layout, addressing scheme, and configurations for a 40-node enterprise route redistribution lab built in EVE-NG. This comprehensive scenario integrates multiple dynamic routing protocols—including a multi-area OSPF backbone, multiple EIGRP autonomous systems, and RIPv2—along with static route injection.

Sample Configuration: Mutual Redistribution
The following is a reference configuration for R31, illustrating mutual route injection between RIPv2 and EIGRP 50.

! --- R31 EIGRP 50 Configuration ---
router eigrp 50
 network 35.0.0.0
 no auto-summary
 ! Redistribute RIP into EIGRP using seed metrics (Bandwidth, Delay, Reliability, Load, MTU)
 redistribute rip metric 100000 10 255 1 1500

! --- R31 RIPv2 Configuration ---
router rip
 version 2
 network 30.0.0.0
 network 31.0.0.0
 no auto-summary
 ! Redistribute EIGRP into RIP using hop-count metric
 redistribute eigrp 50 metric 2