# Memory Pressure Simulation

## Objective
To simulate high memory usage, observe system behavior under memory pressure, and validate recovery after memory-intensive processes terminate.

---

## Baseline Memory Check

### Commands Executed
free -h  
top  

### Output Observed
- Total Memory: 3.6 GiB  
- Used: ~418 MiB  
- Available: ~3.4 GiB  
- Swap: 2.2 GiB total, 0B used  

### Interpretation
System memory usage was within normal limits with no swap utilization.

---

## Memory Stress Simulation

### Command Executed
stress --vm 1 --vm-bytes 2G --timeout 60

### Observed Behavior
- Virtual machine became noticeably slow
- Shell responsiveness decreased
- System performance temporarily degraded

### Interpretation
The stress process allocated approximately 2G of RAM, creating memory pressure. Although swap was not utilized, the system experienced performance degradation due to high memory consumption.

---

## Post-Stress Validation

### Command Executed
free -h

### Output Observed
- Used Memory: ~580 MiB  
- Buff/cache increased to ~324 MiB  
- Swap: 0B used  

### Interpretation
After the stress process terminated, memory usage returned near baseline. Increased buff/cache reflects Linux memory optimization behavior and does not indicate a leak.

---

## Skills Practiced

- Monitoring memory usage using `free` and `top`
- Understanding Linux memory allocation behavior
- Observing system response under memory pressure
- Validating post-incident recovery
- Differentiating between memory usage and swap activity

---

## Conclusion

This simulation demonstrated how high memory allocation impacts system responsiveness. Even without swap usage, memory pressure can temporarily degrade performance. Proper monitoring and validation confirmed full recovery after the stress process completed.
