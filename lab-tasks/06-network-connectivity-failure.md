# Network Connectivity Failure Simulation

## Objective
To simulate a network connectivity failure, investigate the root cause using structured troubleshooting steps, and restore system connectivity.

---

## Baseline Network Validation

### Commands Executed
ip a  
ip route  
ping -c 4 8.8.8.8  

### Output Observed
- Interface `enp0s3` assigned IP: 10.0.2.15/24  
- Default gateway: 10.0.2.2 via enp0s3  
- Ping to 8.8.8.8 successful  
- 4 packets transmitted, 4 received, 0% packet loss  

### Interpretation
Network connectivity was fully operational prior to simulation.

---

## Simulated Network Outage

### Command Executed
sudo ip link set enp0s3 down  

### Output Observed
- Interface `enp0s3` state changed to DOWN  

### Connectivity Test
ping -c 4 8.8.8.8  

### Result
- Error: "connect: Network is unreachable"

### Interpretation
The system was unable to route traffic due to the primary network interface being disabled. This represents a link-level failure scenario.

---

## Root Cause Identification

### Command Executed
ip a  

### Output Observed
- Interface `enp0s3` confirmed in state DOWN  

### Interpretation
The network outage was caused by the primary interface being administratively disabled.

---

## Incident Resolution

### Command Executed
sudo ip link set enp0s3 up  

### Output Observed
- Interface state changed to UP  
- IP address 10.0.2.15/24 reassigned  

---

## Post-Incident Validation

### Command Executed
ping -c 4 8.8.8.8  

### Output Observed
- 4 packets transmitted  
- 4 packets received  
- 0% packet loss  

### Interpretation
Network connectivity was successfully restored. The system regained full external reachability.

---

## Skills Practiced

- Network interface inspection using `ip a`
- Route verification using `ip route`
- Connectivity testing using `ping`
- Identifying link-down conditions
- Root cause validation
- Structured incident recovery workflow

---

## Conclusion

This exercise simulated a real-world network outage caused by a disabled network interface. The investigation followed a structured troubleshooting approach, leading to successful restoration of connectivity.
