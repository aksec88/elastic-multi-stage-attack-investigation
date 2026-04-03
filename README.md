# 30-Day SOC Lab — Elastic SIEM

## Elastic Stack SOC Challenge

**5.8M+ Events | 222K+ Attacks | 4 Detection Rules | C2 Simulation**
---

## Key Highlights

- High-volume brute-force activity observed across SSH and RDP services  
- Attack traffic originated from hundreds of global IP addresses  
- Privileged accounts (Administrator, root) were primary targets  
- Successful compromise achieved via weak RDP credentials  
- Full attack chain executed and validated (initial access → exfiltration)  
- Custom detection rules successfully identified all attack stages   

---

## Overview

Built and operated a cloud-based Security Operations Center using the Elastic Stack over a 30-day period.  

Simulated real-world attacks using Mythic C2, ingested multi-source telemetry, engineered detections, and performed incident investigations across authentication, endpoint, and network data.  

All activity was performed in a controlled lab environment with internet-exposed services to capture real-world attack traffic.

---

## Architecture

- **Elastic Stack (Elasticsearch + Kibana)** — SIEM for log aggregation, search, and alerting  
- **Fleet Server + Elastic Agent** — endpoint telemetry collection and management  
- **Windows Server & Ubuntu Linux** — monitored endpoints and attack targets  
- **Mythic C2 Framework (Apollo)** — adversary simulation and post-exploitation  
- **osTicket** — alert-to-ticket automation and incident tracking  

---

## What I Did

- Deployed and configured a full SIEM environment in the cloud  
- Ingested logs from Windows (Sysmon, Security logs) and Linux (auth logs)  
- Engineered detection rules for:
  - SSH brute-force attacks  
  - RDP brute-force attacks  
  - Mythic Apollo C2 agent execution  
- Simulated a full attack chain:
  - Initial access (RDP brute force)  
  - Discovery and privilege validation  
  - Defense evasion (Defender disabled)  
  - Payload delivery via PowerShell  
  - Command-and-control communication  
  - Data exfiltration  
- Investigated alerts using process correlation (Sysmon Event ID 1 & 3)  
- Extracted and validated IOCs (file hashes, IPs, process artifacts)  
- Integrated automated alerting with osTicket  
- Deployed Elastic Defend for endpoint detection and response  

---

## Key Investigation Highlight

Reconstructed a complete attack timeline from initial access to data exfiltration:

- RDP brute-force → successful Administrator login  
- PowerShell payload download from C2 infrastructure  
- Execution of masqueraded binary (`svchost-aksec.exe`)  
- Persistent C2 communication established  
- Data exfiltration via C2 channel  

**Total time to compromise: ~25 minutes**

---

## Detection Engineering

Developed and validated custom detection rules:

- SSH brute-force detection (threshold-based)  
- RDP brute-force detection (Event ID 4625 correlation)  
- C2 detection using hash + filename matching (Apollo agent)  
- Behavioral monitoring of PowerShell, cmd, and rundll32 activity  

All detection rules successfully identified attack activity with low false positives.

---

## Deep Dive Sections

- [Detection Engineering](./detection.md)  
- [Incident Investigation](./investigation.md)  
- [Architecture & Setup](./architecture.md)  
- [Dashboards & Visualizations](./dashboards.md)  

---

## Author

**Abdul Kuyateh — SOC Analyst**
