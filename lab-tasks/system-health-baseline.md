# System Health Baseline – Initial Validation

## Objective
Establish an initial system performance baseline after server provisioning to support future anomaly detection and incident comparison.

---

## Uptime & Load Average

**Command Executed:**
uptime

**Output:**
- Uptime: 32 minutes  
- Load Average: 0.02, 0.01, 0.00  

**Interpretation:**
The system has been running continuously since installation with no unexpected restarts.  
Load averages are significantly below the 2.00 threshold for a 2-core system, indicating no CPU contention or processing backlog.  
The server is operating in a stable and idle state.

---

## Memory Utilization

**Command Executed:**
free -h

**Output:**
- Used Memory: 458Mi  
- Shared Memory: 1.1Mi  
- Swap Usage: 0B  

**Interpretation:**
Memory consumption is within expected baseline levels for a newly provisioned Ubuntu Server instance.  
No swap usage observed, indicating no memory pressure or resource exhaustion.

---

## Disk Utilization

**Command Executed:**
df -h

**Output:**
- /dev/mapper/ubuntu--vg--ubuntu--lv: 46% utilized  

**Interpretation:**
Disk utilization is well below operational alert thresholds (80% warning, 90% critical).  
No storage constraints detected at this time.

---

## Process & CPU State

**Command Executed:**
top

**Output Observations:**
- Total Processes: 118  
- Running: 1  
- Sleeping: 117  
- Zombie: 0  
- CPU Usage: 0.0%  
- Top Process: PID 1 (systemd)

**Interpretation:**
System process state is stable with no abnormal or zombie processes detected.  
CPU utilization is minimal, confirming idle baseline conditions.  
PID 1 (systemd) resource usage is within expected normal parameters.

---

## Baseline Conclusion

The system is operating under stable and healthy conditions with no signs of resource contention, abnormal process behavior, or storage concerns.  

This baseline snapshot will serve as a reference point for future monitoring comparisons and incident investigations.
