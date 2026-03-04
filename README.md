# Infra NOC Home Lab

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

# Lab Objectives

This project focuses on building practical skills in:

- Linux system monitoring  
- Infrastructure troubleshooting  
- Network diagnostics  
- DNS issue isolation  
- Service outage recovery  
- Incident investigation workflow  
- Root cause analysis  

---

# Lab Scenarios

## Day 1 – Environment Setup & Service Installation

- Installed Ubuntu Server in VirtualBox  
- Configured networking  
- Installed and verified Nginx web server  
- Performed initial system health validation  

---

## Day 2 – CPU Spike Simulation

- Simulated high CPU usage using test processes  
- Investigated CPU consumption using `top`  
- Identified high-usage processes  
- Restored system stability  

---

## Day 3 – Disk Space Exhaustion

- Created large files to simulate disk usage growth  
- Investigated disk usage using `df` and `ls`  
- Identified storage consumption  
- Removed test files and restored disk capacity  

---

## Day 4 – Memory Pressure Simulation

- Generated memory load using the `stress` tool  
- Observed system slowdown under memory pressure  
- Investigated process memory usage using `top`  
- Confirmed system recovery after load removal  

---

## Day 5 – Network & DNS Troubleshooting

Simulated multiple network incidents.

### Interface Failure

- Disabled primary network interface  
- Observed **Network is unreachable**  
- Investigated using `ip a` and routing checks  
- Restored interface connectivity  

### DNS Failure

- Modified DNS configuration using `resolvectl`  
- Observed **Temporary failure in name resolution**  
- Verified network connectivity vs DNS failure  
- Restored DNS servers and validated resolution  

---

## Day 6 – Service Outage Simulation (Nginx)

### Scenario 1 – Service Stopped

- Stopped nginx service  
- Observed service unreachable  
- Investigated using `systemctl`  
- Restored service and validated HTTP response  

### Scenario 2 – Configuration Failure

- Introduced invalid nginx directive  
- Detected configuration error using `nginx -t`  
- Observed service startup failure  
- Investigated logs using `journalctl`  
- Corrected configuration and restored service  

---

# Repository Structure

```
infra-noc-home-lab/
│
├── lab-setup/
│   └── environment-setup.md
│
├── lab-tasks/
│   ├── 02-cpu-spike-simulation.md
│   ├── 03-disk-exhaustion.md
│   ├── 04-memory-pressure.md
│   ├── 06-network-troubleshooting-simulation.md
│   └── 07-nginx-service-failure-simulation.md
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

# Future Lab Scenarios

Planned extensions for this lab include:

- Firewall rule misconfiguration  
- Port conflict preventing service startup  
- Log-based incident investigation  
- Monitoring and alert simulation  
- Application performance troubleshooting  

---

# Purpose of This Project

This project is intended to demonstrate **hands-on troubleshooting ability** for roles such as:

- Infrastructure Operations Analyst  
- NOC Engineer  
- Technical Support Engineer  
- Systems Operations Specialist  

Each lab scenario reflects real operational incidents and focuses on structured diagnosis and recovery methods used in production environments.
