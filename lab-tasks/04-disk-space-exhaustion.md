# Disk Space Exhaustion Simulation

## Objective
To simulate a disk space exhaustion incident, investigate potential causes, identify the root cause, and restore system storage using Linux monitoring and troubleshooting commands.

---

## Baseline Disk Check

### Command Executed
df -h

### Output Observed
- Filesystem: /dev/mapper/ubuntu--vg-ubuntu--lv mounted on `/`
- Total Size: 12G
- Used: 5.2G
- Available: 5.6G
- Usage: 49%

### Interpretation
Disk usage was within normal operating limits and no immediate storage risk was observed.

### Baseline Snapshot
![Day-4 Baseline](../assets/screenshots/day-4/day-4-baseline.png)

---

## Disk Consumption Simulation

### Commands Executed
sudo fallocate -l 1G largefile1.img  
sudo fallocate -l 1G largefile2.img  
sudo fallocate -l 1G largefile3.img  

### Output Observed
- Disk usage increased gradually
- Final usage reached approximately 77%

### Interpretation
This simulated a high disk utilization alert scenario caused by rapid storage consumption.

### Exhaustion Snapshot
![Day-4 Exhaustion](../assets/screenshots/day-4/day-4-exhaustion.png)

---

## Alert Validation

### Command Executed
df -h

### Output Observed
- Disk usage confirmed at 77%

### Interpretation
Disk utilization crossed warning threshold levels and required investigation.

---

## Initial Investigation

### Command Executed
ls -lh /

### Output Observed
- Observed `swap.img` consuming approximately 2.3G

### Interpretation
Although `swap.img` appeared large, it is a system-managed swap file and not the cause of sudden disk growth.  
This step highlights the importance of validating system files before taking corrective action.

### Root Directory Snapshot
![Day-4 Root Check](../assets/screenshots/day-4/day-4-root-check.png)

---

## Directory Verification

### Command Executed
pwd

### Output Observed
- Confirmed current working directory was `/home/aceak`

### Command Executed
ls -lh

### Output Observed
- Identified multiple `largefile*.img` files
- Each file approximately 1.0G

### Interpretation
The disk usage spike was caused by large user-created files consuming storage within the home directory.

### Large Files Snapshot
![Day-4 Large Files](../assets/screenshots/day-4/day-4-largefiles.png)

---

## Controlled Incident Resolution

### Command Executed
rm largefile1.img

### Output Observed
- Disk usage reduced from 77% to 67%

### Interpretation
Initial cleanup confirmed that the identified files were the root cause of disk exhaustion.

### Partial Cleanup Snapshot
![Day-4 Partial Cleanup](../assets/screenshots/day-4/day-4-partial-cleanup.png)

---

## Complete Cleanup

### Command Executed
rm largefile*.img

### Output Observed
- Disk usage returned to baseline levels

---

## Post-Incident Validation

### Command Executed
df -h

### Output Observed
- Used: 5.2G
- Available: 5.6G
- Usage: 49%

### Interpretation
System storage was fully restored, confirming successful incident resolution.

### Final Validation Snapshot
![Day-4 Restored](../assets/screenshots/day-4/day-4-restored.png)

---

## Skills Practiced

- Disk monitoring using `df`
- File inspection using `ls`
- Directory verification using `pwd`
- Differentiating system-managed files from user-generated growth
- Controlled cleanup procedures
- Post-incident validation workflow

---

## Conclusion

This exercise simulated a real-world disk exhaustion incident.  
The investigation required distinguishing between system-managed files and abnormal user-generated storage growth, followed by controlled cleanup and validation of system recovery.

The incident lifecycle followed:

Detection → Validation → Investigation → Root Cause Identification → Controlled Remediation → Post-Incident Verification
