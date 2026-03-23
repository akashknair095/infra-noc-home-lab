# Infra-NOC Home Lab

> **12 incident scenarios** across CPU, memory, disk, network, and service layers  
> **Capstone multi-fault incident** with structured root cause isolation  
> **Full screenshot evidence** for every scenario  
> **Tools:** `systemctl` · `journalctl` · `ss` · `ufw` · `nginx` · `top` · `curl` · `df` · `free` · `ip`

---

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

`systemctl` `journalctl` `ss` `curl` `top` `free` `df` `du` `ip` `ping` `ufw` `nginx -t` `stress` `resolvectl`

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

1. Baseline Verification
2. Incident Simulation
3. Failure Observation
4. Investigation (Logs and Validation)
5. Root Cause Identification
6. Resolution
7. Validation

---

## Documentation Approach

Each scenario includes:

- Commands executed
- Output observations
- Screenshots as evidence
- Interpretation of findings
- Resolution steps

---

## Skills Demonstrated

- System-level troubleshooting
- Service lifecycle management
- Log-based debugging
- Network diagnostics
- Firewall rule validation
- Performance analysis
- Structured incident response

---

## Outcome

This project demonstrates the ability to:

- Troubleshoot real-world infrastructure issues using a structured approach
- Analyze system behavior using logs, monitoring tools, and service validation
- Identify root causes in multi-layer incidents with environmental noise
- Restore services efficiently while validating system stability

---

## Author

**Akash K**  
Aspiring Infrastructure / NOC Analyst  
Actively building hands-on experience in Linux systems, monitoring, and incident response.
