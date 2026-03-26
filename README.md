# Infra-NOC Home Lab
 
![Platform](https://img.shields.io/badge/Platform-VirtualBox-blue) ![OS](https://img.shields.io/badge/OS-Ubuntu-orange) ![Service](https://img.shields.io/badge/Service-Nginx-green)
 
## Project Overview
 
This project simulates real-world Network Operations Center (NOC) scenarios using a Linux-based lab environment. It demonstrates hands-on troubleshooting, monitoring, and incident resolution across multiple system layers.
 
The objective is to build practical, job-ready skills in diagnosing infrastructure issues using a structured and methodical approach.
 
---
 
## Key Focus Areas
 
- Linux system administration
- Service monitoring and troubleshooting
- Incident lifecycle management
- Log analysis and root cause identification
- Network and port-level diagnostics
- Firewall configuration and validation
- Performance and resource monitoring
 
---
 
## Lab Environment
 
- **Operating System:** Ubuntu (Virtual Machine)
- **Platform:** Oracle VirtualBox
- **Service:** Nginx
 
### Tools Used
 
`systemctl` · `journalctl` · `ss` · `curl` · `top` · `free` · `df` · `du` · `ps` · `ip` · `ping` · `resolvectl` · `ufw` · `nginx -t` · `stress`
 
---
 
## How to Use This Repo
 
1. Set up Ubuntu on Oracle VirtualBox (any recent LTS release works).
2. Install Nginx: `sudo apt install nginx`.
3. Clone this repo and navigate to `lab-tasks/`.
4. Follow each numbered task file in order — each is self-contained with setup, simulation, and resolution steps.
5. Screenshots referenced in tasks are available in `assets/screenshots/`.
 
---
 
## Repository Structure
 
```
infra-noc-home-lab/
├── assets/
│   └── screenshots/
├── lab-setup/
├── lab-tasks/
│   ├── 01-system-health-baseline.md
│   ├── 02-nginx-service-incident.md
│   ├── 03-cpu-spike-simulation.md
│   ├── 04-disk-space-exhaustion.md
│   ├── 05-memory-exhaustion-simulation.md
│   ├── 06-network-troubleshooting-simulation.md
│   ├── 07-nginx-service-failure-simulation.md
│   ├── 08-port-conflict-simulation.md
│   ├── 09-nginx-binding-misconfiguration.md
│   ├── 10-nginx-configuration-failure.md
│   ├── 11-firewall-access-control.md
│   └── 12-capstone-integrated-incident-response.md
└── README.md
```
 
---
 
## Lab Breakdown
 
### Day 1: System Health Baseline
Established baseline metrics for CPU, memory, disk, and running services using `top`, `free`, `df`, and `ps`. Captured reference state before any incident simulation.
 
### Day 2: Nginx Service Incident
Installed and validated the nginx service, simulated a service outage, and investigated service state using `systemctl`. Restored service availability and verified recovery.
 
### Day 3: CPU Spike Simulation
Generated high CPU load using stress processes and identified resource-intensive processes using `top`. Investigated root cause and restored system stability after load removal.
 
### Day 4: Disk Space Exhaustion
Simulated a disk-full condition by creating large files, investigated usage using `df` and `du`, and recovered disk capacity by identifying and removing test artifacts.
 
### Day 5: Memory Pressure Simulation
Generated memory load using the `stress` tool, observed system behavior under pressure, and investigated memory consumption using `free` and `top`. Confirmed system recovery after load removal.
 
### Day 6: Network Troubleshooting
Simulated two network incidents — interface failure (disabled NIC, investigated with `ip`) and DNS resolution failure (modified DNS config, isolated using `resolvectl` and `ping`). Restored connectivity for both scenarios.
 
### Day 7: Nginx Service Failure
Simulated two nginx failure modes: service stopped (recovered via `systemctl`) and configuration syntax error (detected via `nginx -t`, investigated with `journalctl`, corrected and restarted). Validated availability after each recovery.
 
### Day 8: Port Conflict and Service Failure
Simulated port binding conflict by occupying port 80 with a Python HTTP server. Identified the conflict using `ss`, resolved it by terminating the conflicting process, restarted nginx, and validated service availability.
 
### Day 9: Nginx Binding Misconfiguration
Diagnosed an accessibility failure caused by nginx binding to an incorrect network interface. Identified the misconfiguration through config inspection and corrected the listening address to restore service access.
 
### Day 10: Configuration Syntax Failure
Introduced an invalid nginx directive and detected the resulting startup failure using `nginx -t` and `journalctl`. Corrected the configuration syntax and validated successful service restoration.
 
### Day 11: Firewall Access Control
Applied and tested firewall rules using `ufw`. Analyzed traffic behavior under NAT limitations, validated rule enforcement, and confirmed expected access control outcomes.
 
### Day 12: Capstone – Integrated Incident Response
Simulated a multi-layer incident involving a service failure, nginx configuration error, and concurrent CPU load (noise). Performed structured triage to isolate the configuration failure as the true root cause — distinguishing it from the CPU noise — then restored full service availability and validated recovery.
 
---
 
## Incident Handling Workflow
 
Each lab follows a structured troubleshooting approach:
 
1. **Baseline Verification** — Confirm known-good state before simulation
2. **Incident Simulation** — Introduce controlled failure
3. **Failure Observation** — Document symptoms and system behavior
4. **Investigation** — Analyze logs, service state, and configuration
5. **Root Cause Identification** — Pinpoint the underlying cause
6. **Resolution** — Apply targeted fix
7. **Validation** — Confirm full recovery and system stability
 
---
 
## Documentation Approach
 
Each scenario includes:
 
- Commands executed with context
- Output observations and interpretation
- Screenshots as evidence
- Root cause analysis
- Resolution steps and validation
 
---
 
## Skills Demonstrated
 
This project demonstrates the ability to:
 
- Troubleshoot real-world infrastructure issues using a structured, repeatable methodology
- Analyze system behavior through logs, monitoring tools, and service validation
- Identify root causes in multi-layer incidents, including distinguishing true failures from environmental noise
- Restore services efficiently while confirming system stability
- Apply firewall rules and validate access control behavior
- Diagnose network-level failures across interface and DNS layers
 
---
 
## Author
 
**Akash K**  
Aspiring Infrastructure / NOC Analyst  
Actively building hands-on experience in Linux systems, monitoring, and incident response.
 
[LinkedIn](https://www.linkedin.com/in/akash-k-2078072b7/)
