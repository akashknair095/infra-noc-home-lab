# Infra NOC Home Lab

A hands-on Infrastructure Operations lab that simulates real-world NOC incidents including CPU spikes, disk exhaustion, DNS failures, service outages, and port conflicts using Linux troubleshooting workflows.

**Key Skills:** Linux Troubleshooting • Incident Investigation • Network Diagnostics • Service Recovery • Infrastructure Monitoring

---

## Overview

This project documents a hands-on **Infrastructure / NOC home lab** designed to simulate real-world operational incidents in a Linux environment.

The goal of this lab is to practice **monitoring, troubleshooting, and restoring system services** using structured investigation workflows similar to those used by Network Operations Centers (NOCs) and Infrastructure teams.

Each lab scenario reproduces a common production incident such as CPU spikes, disk exhaustion, network failures, or service outages. Every scenario includes the investigation process, root cause identification, and recovery validation.

---

# Lab Environment

**Platform**
- Oracle VirtualBox

**Operating System**
- Ubuntu Server

**Services Used**
- Nginx Web Server

**Primary Tools**
- `top`
- `free`
- `df`
- `du`
- `ss`
- `curl`
- `ping`
- `ip`
- `systemctl`
- `journalctl`
- `resolvectl`
- `stress`

---

# Lab Progress

| Day | Scenario | Lab File |
|----|----|----|
| Day 1 | System Health Baseline | `01-system-health-baseline.md` |
| Day 2 | Nginx Service Incident | `02-nginx-service-incident.md` |
| Day 3 | CPU Spike Simulation | `03-cpu-spike-simulation.md` |
| Day 4 | Disk Space Exhaustion | `04-disk-space-exhaustion.md` |
| Day 5 | Memory Pressure Simulation | `05-memory-exhaustion-simulation.md` |
| Day 6 | Network Troubleshooting | `06-network-troubleshooting-simulation.md` |
| Day 7 | Nginx Service Failure | `07-nginx-service-failure-simulation.md` |
| Day 8 | Port Conflict Simulation | `08-port-conflict-simulation.md` |

---

# Lab Scenarios

## Day 1 – System Health Baseline
- Established baseline system health metrics
- Checked CPU, memory, disk, and process statistics
- Verified system resource availability before simulations

---

## Day 2 – Nginx Service Incident
- Installed and validated nginx service
- Simulated a service outage
- Investigated service state using `systemctl`
- Restored service availability

---

## Day 3 – CPU Spike Simulation
- Simulated high CPU load using test processes
- Identified high CPU usage using `top`
- Investigated processes consuming CPU resources
- Restored system stability

---

## Day 4 – Disk Space Exhaustion
- Created large files to simulate disk usage growth
- Investigated disk usage using `df`
- Identified storage consumption using file inspection
- Removed test files to restore disk capacity

---

## Day 5 – Memory Pressure Simulation
- Generated memory load using the `stress` tool
- Observed system slowdown under memory pressure
- Investigated memory consumption using monitoring tools
- Confirmed system recovery after load removal

---

## Day 6 – Network Troubleshooting
Simulated network related incidents including:

### Interface Failure
- Disabled primary network interface
- Observed connectivity failures
- Investigated interface status using `ip`
- Restored network connectivity

### DNS Resolution Failure
- Modified DNS configuration
- Observed name resolution failure
- Verified connectivity vs DNS resolution
- Restored correct DNS servers

---

## Day 7 – Nginx Service Failure

### Scenario 1 – Service Stopped
- Stopped nginx service
- Observed service unreachable
- Investigated service state using `systemctl`
- Restarted service and validated availability

### Scenario 2 – Configuration Failure
- Introduced invalid nginx directive
- Detected configuration error using `nginx -t`
- Observed service startup failure
- Investigated logs using `journalctl`
- Corrected configuration and restored service

---

## Day 8 – Port Conflict Simulation
- Stopped nginx service
- Started a Python HTTP server occupying port 80
- Attempted to start nginx and observed port binding failure
- Identified port conflict using `ss`
- Resolved conflict by stopping the conflicting service
- Restarted nginx and validated service availability

---

# Repository Structure

```
infra-noc-home-lab/
│
├── lab-setup/
│
├── lab-tasks/
│   ├── 01-system-health-baseline.md
│   ├── 02-nginx-service-incident.md
│   ├── 03-cpu-spike-simulation.md
│   ├── 04-disk-space-exhaustion.md
│   ├── 05-memory-exhaustion-simulation.md
│   ├── 06-network-troubleshooting-simulation.md
│   ├── 07-nginx-service-failure-simulation.md
│   └── 08-port-conflict-simulation.md
│
└── README.md
```

---

# Skills Demonstrated

Through these labs the following operational skills were practiced:

- Linux system monitoring  
- Incident investigation workflows  
- Service troubleshooting  
- Network diagnostics  
- DNS issue isolation  
- Log analysis  
- Configuration validation  
- Service restoration and verification  

---

# Purpose of This Project

This project is intended to demonstrate **hands-on troubleshooting ability** for roles such as:

- Infrastructure Operations Analyst  
- NOC Engineer  
- Technical Support Engineer  
- Systems Operations Specialist  

Each lab scenario reflects real operational incidents and focuses on structured diagnosis and recovery methods used in production environments.

This project is continuously expanded with additional troubleshooting scenarios to simulate real-world NOC operational incidents.