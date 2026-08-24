Overview
This repository contains the configuration and topology files for a 9-node, highly meshed Cisco routing environment. Built specifically for the EVE-NG network emulation platform using Cisco IOL (IOS on Linux) images, this lab provides a functional baseline for testing dynamic routing using the Routing Information Protocol version 2 (RIPv2).

Introduction
This project is designed for network engineers and students who want to study the mechanics of distance-vector routing protocols within a complex, multi-path topology.
By deploying this lab, you can observe firsthand how RIPv2 handles prefix advertisement, network convergence during simulated link failures, and classless routing with auto-summarization disabled. The included XML-based .unl topology file comes pre-loaded with base64 startup configurations for all 9 routers, ensuring you can immediately boot the environment and begin verifying routing tables.