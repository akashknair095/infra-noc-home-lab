# Infra-NOC Home Lab

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

- Operating System: Ubuntu (Virtual Machine)
- Platform: Oracle VirtualBox
- Service: Nginx

### Tools Used

- systemctl
- journalctl
- ss
- curl
- top, free
- ufw
- nginx -t

---
## Repository Structure

The repository is organized into setup configuration, task-based lab exercises, and supporting assets:

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
Established baseline metrics for CPU, memory, disk, and running services.

### Day 2: Nginx Service Incident
Simulated service failure and performed initial troubleshooting using system tools.

### Day 3: CPU Spike Simulation
Generated high CPU load and analyzed system behavior under stress.

### Day 4: Disk Space Exhaustion
Simulated disk full condition and performed cleanup and recovery.

### Day 5: Log Analysis
Investigated system logs to identify service and configuration issues.

### Day 6: Service Recovery
Restored failed services using structured troubleshooting methodology.

### Day 7: Monitoring Basics
Explored system monitoring tools and process-level visibility.

### Day 8: Port Conflict and Service Failure
Simulated port binding conflict and resolved service startup failure.

### Day 9: Nginx Binding Misconfiguration
Diagnosed accessibility issues caused by incorrect interface binding.

### Day 10: Configuration Syntax Failure
Detected and resolved nginx configuration errors using validation and logs.

### Day 11: Firewall Access Control
Applied firewall rules and analyzed behavior under NAT limitations.

### Day 12: Capstone – Integrated Incident Response and Monitoring
Simulated a multi-layer incident involving service failure, configuration error, and CPU load. 
Demonstrated root cause isolation by distinguishing between actual failure and environmental noise, followed by full service restoration.

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
- Identify root causes in multi-layer incidents  
- Restore services efficiently while validating system stability  

---

## Author

Akash K  
Aspiring Infrastructure / NOC Analyst
Actively building hands-on experience in Linux systems, monitoring, and incident response.
