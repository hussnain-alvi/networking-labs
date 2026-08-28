Multi-Protocol Enterprise Network Topology | EVE-NG / Cisco

Overview
This repository contains the topology layout, addressing scheme, and configurations for a 40-node enterprise route redistribution lab built in EVE-NG. This comprehensive scenario integrates multiple dynamic routing protocols—including a multi-area OSPF backbone, multiple EIGRP autonomous systems, and RIPv2—along with static route injection.

Situation & Task: Designed a complex routing simulation integrating OSPF (4 areas), EIGRP (2 processes), and RIPv2 to bridge disparate routing domains and ensure seamless communication.
Action: Configured device IP addressing, dynamic routing protocols, and boundary redistribution parameters across the multi-router architecture.
Result: Successfully established end-to-end connectivity, verified by error-free packet traversal and ping validation from an OSPF-10 host to EIGRP-50 and switch-connected endpoints.

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
