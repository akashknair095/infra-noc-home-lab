# Firewall Blocking HTTP Access (UFW)

## Objective

Simulate a scenario where firewall rules restrict HTTP access to a running nginx service and analyze the behavior under a virtualized environment.

---

## Baseline Service Check

### Command Executed
ip a  
sudo systemctl status nginx  
curl -I localhost  
curl -I http://10.0.2.15  

### Output Observed
- System assigned IP address (10.0.2.15)
- Active: active (running)
- HTTP/1.1 200 OK (localhost)
- HTTP/1.1 200 OK (IP)

### Baseline Snapshot

![Network Baseline](../assets/screenshots/day-11/day-11-network-baseline.png)

![Service Baseline](../assets/screenshots/day-11/day-11-service-baseline.png)

### Interpretation
The system network and nginx service were functioning normally, and the application was accessible both locally and via IP address.

---

## Firewall Configuration

### Command Executed
sudo ufw enable  
sudo ufw status  

### Output Observed
- Status: active
- No rules configured initially

### Firewall Enabled

![UFW Enabled](../assets/screenshots/day-11/day-11-ufw-enabled-clean.png)

### Interpretation
Firewall was enabled in a clean state with no restrictions applied.

---

## Firewall Rule Application

### Command Executed
sudo ufw default deny incoming  
sudo ufw allow ssh  
sudo ufw deny 80  
sudo ufw status  

### Output Observed
- Default: deny (incoming)
- 22/tcp ALLOW
- 80 DENY

### Firewall Rules Applied

![UFW Rules Applied](../assets/screenshots/day-11/day-11-ufw-rules-applied.png)

### Interpretation
Firewall rules were configured to block HTTP traffic while allowing SSH access.

---

## Connectivity Test After Firewall Rules

### Command Executed
curl -I localhost  
curl -I http://10.0.2.15  

### Output Observed
- HTTP/1.1 200 OK (localhost)
- HTTP/1.1 200 OK (IP)

### Connectivity Snapshot

![Firewall Test](../assets/screenshots/day-11/day-11-firewall-test.png)

### Interpretation
Despite firewall rules denying port 80, the service remained accessible.

---

## Investigation

### Command Executed
sudo ss -tulpn | grep :80  

### Output Observed
- nginx listening on 0.0.0.0:80
- nginx listening on [::]:80

### Port Verification

![Port Verification](../assets/screenshots/day-11/day-11-port-verification.png)

### Interpretation
The nginx service was correctly bound to all interfaces and functioning normally.

---

## Root Cause Analysis

### Finding
- Firewall rules were correctly applied
- Traffic was not being blocked as expected

### Root Cause
- Requests were initiated from the same host
- Local traffic does not traverse the firewall as external incoming traffic
- NAT networking further restricts external traffic simulation

### Interpretation
The firewall did not block the request due to local traffic behavior and virtualization limitations.

---

## Resolution

### Command Executed
sudo ufw allow 80  
sudo ufw status  

### Output Observed
- 80/tcp ALLOW

### Interpretation
HTTP access explicitly allowed through firewall rules.

---

## Service Validation

### Command Executed
curl -I http://10.0.2.15  

### Output Observed
- HTTP/1.1 200 OK

### Service Restored

![Service Restored](../assets/screenshots/day-11/day-11-firewall-test.png)

### Interpretation
HTTP access confirmed after allowing port 80.

---

## Skills Practiced

- Firewall configuration using UFW
- Understanding local vs external traffic behavior
- Network troubleshooting in virtual environments
- Service validation using curl
- Port inspection using ss
- Root cause analysis

---

## Conclusion

This exercise demonstrated firewall configuration and highlighted the difference between local and external traffic behavior. Although HTTP access was not blocked due to NAT-based virtualization, the investigation provided insight into real-world firewall behavior and network flow.
