# System Health Baseline – Initial Validation

## Objective
Establish an initial system performance baseline after server provisioning to support future anomaly detection and incident comparison.

---

## Uptime & Load Average

**Command Executed:**
uptime

**Output:**
- Uptime: 13 minutes  
- Load Average: 0.00, 0.00, 0.00  

### Uptime Baseline

![Uptime Baseline](../assets/screenshots/day-1/day-1-uptime-baseline.png)

**Interpretation:**
The system has been running continuously since installation with no unexpected restarts.  
Load averages are significantly below the 2.00 threshold for a 2-core system, indicating no CPU contention or processing backlog.  
The server is operating in a stable and idle state.

---

## Memory Utilization

**Command Executed:**
free -h

**Output:**
- Total Memory: 3.8Gi  
- Used Memory: 390Mi  
- Free Memory: 3.4Gi  
- Shared Memory: 1.0Mi  
- Buff/Cache: 296Mi  
- Available Memory: 3.4Gi  
- Swap Usage: 0B  

**Interpretation:**
Memory consumption is within expected baseline levels for a newly provisioned Ubuntu Server instance.  
No swap usage observed, indicating no memory pressure or resource exhaustion.

---

## Disk Utilization

**Command Executed:**
df -h

**Output:**
- /dev/mapper/ubuntu--vg-ubuntu--lv  
  - Size: 12G  
  - Used: 5.0G  
  - Available: 5.7G  
  - Usage: 47%

### Memory and Disk Baseline

![Memory and Disk Baseline](../assets/screenshots/day-1/day-1-memory-disk.png)

**Interpretation:**
Disk utilization is well below operational alert thresholds (80% warning, 90% critical).  
No storage constraints detected at this time.

---

## Process & CPU State

**Command Executed:**
top

**Output Observations:**
- Total Processes: 114  
- Running: 1  
- Sleeping: 113  
- Zombie: 0  
- CPU Idle: 100.0%  
- Top Process: PID 1 (systemd)

### Process and CPU Baseline

![Top Baseline](../assets/screenshots/day-1/day-1-top-baseline.png)

**Interpretation:**
System process state is stable with no abnormal or zombie processes detected.  
CPU utilization remains idle at 100%, confirming baseline stability.  
PID 1 (systemd) resource usage is within expected normal parameters.

---

## Baseline Conclusion

The system is operating under stable and healthy conditions with no signs of resource contention, abnormal process behavior, or storage concerns.  

This baseline snapshot will serve as a reference point for future monitoring comparisons and incident investigations.
