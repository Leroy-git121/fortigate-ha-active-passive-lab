# FortiGate HA (Active–Passive) Lab


A simple, image-driven walkthrough for configuring **High Availability (HA) Active–Passive** on FortiGate,
ideal for lab environments (EVE‑NG, home lab, or VM deployments).

This repo contains annotated screenshots to help you reproduce the setup quickly.


## Quickstart: FortiGate HA (Active–Passive)

> ⚠️ **Lab safety:** Use a non-production environment. Backup device configs before testing.

### 1) Prereqs
- Two FortiGate instances with identical firmware builds
- Overlapping hardware/VM resources (same model/VM size)
- Dedicated **HA heartbeat** links between the pair
- Consistent interface mappings (WAN/LAN)
- Time sync enabled (NTP)

### 2) Base config on both units
- Set hostname and admin password
- Configure management IPs (temporarily distinct)
- Enable NTP; set timezone
- Ensure both can reach each other on the heartbeat links

### 3) Configure HA on the primary (future **Master**)
GUI path: **System → HA**  
- **Mode**: `Active-Passive`  
- **Group name**: e.g., `FGT_HA_LAB`  
- **Group ID**: any integer (ensure both units match)  
- **Password**: shared cluster password  
- **Heartbeat interfaces**: select two dedicated ports  
- **Device priority**: higher value = preferred master  
- **Monitor interfaces**: select WAN/LAN ports to track link status

### 4) Configure HA on the secondary
- Use the *same* Group name, Group ID, and password
- Set **Device priority** lower than the primary

### 5) Verify cluster formation
- Wait for sync; both units should show **Master**/**Slave** roles
- Check **System → HA** for status (uptime, heartbeat, monitored ports)
- Confirm config sync (checksum matches)

### 6) Data plane checks
- Ensure virtual MACs appear on downstream switches
- Verify upstream gateway ARP points to the cluster
- Test traffic through the cluster (ping/HTTP)

### 7) Failover test
- Pull a monitored interface or power off the Master
- Observe Slave become Master
- Confirm traffic continuity (some seconds of convergence is normal)

### 8) Post‑checks & hygiene
- Re-enable the recovered unit; verify it returns to Slave (if priority favors original Master)
- Save configs; export tech support files if needed
