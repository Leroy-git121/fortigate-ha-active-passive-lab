
# FortiGate HA Active–Passive Lab (Intro)

This repository contains a simple demonstration of setting up **FortiGate High Availability (HA) in Active–Passive mode**.  
It is built in a virtual lab environment and serves as a reference for students, lab enthusiasts, and professionals experimenting with FortiGate clustering.

## Tools & Environment Used
- **EVE-NG** (Emulated Virtual Environment for Next Generation labs)
- **FortiGate VM** (FG-VM64)
- **VMware Workstation / ESXi** (for running the virtual appliances)
- **Windows Server / Client** (test host for LAN connectivity)
- **vSwitch / EVE-NG switch objects** (for LAN/WAN/Heartbeat connections)

## Topology

Below is the high-level topology used in this lab:

          /--[Firewall 1]--\
[R1]------       |   |      ------[WAN]
          \--[Firewall 2]--/

- Two FortiGate firewalls in **Active–Passive HA** cluster
- Heartbeat links between the pair for failover synchronization
- LAN side connected to internal client(s)
- WAN side connected to external router/cloud

## Setup Guide

➡️ Detailed setup steps will be added later.  
(Currently this README is a placeholder for environment details and topology reference.)

## Repository Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/fortigate-ha-active-passive-lab.git
   cd fortigate-ha-active-passive-lab
   ```

2. Use the screenshots and topology to replicate the environment in your own lab.


✍️ *This file is a lightweight intro. For the full HA setup guide, see the main `README.md`.*
