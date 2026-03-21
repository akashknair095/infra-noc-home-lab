# Nginx Service Binding Misconfiguration

## Objective
To simulate a scenario where nginx is running but bound only to the localhost interface, making it inaccessible via the server’s IP address.

---

## Baseline Verification

### Commands Executed
sudo systemctl status nginx  
curl -I localhost  
curl http://10.0.2.15  

### Output Observed
- Service status: **active (running)**  
- Localhost response: **200 OK**  
- IP-based access: **working**

### Baseline Evidence

![Nginx Running](../assets/screenshots/day-9/day-9-nginx-running.png)  
![Localhost Working](../assets/screenshots/day-9/day-9-localhost-working.png)  
![IP Working](../assets/screenshots/day-9/day-9-ip-working.png)

### Interpretation
The nginx service was operating normally and accessible via both localhost and system IP.

---

## Incident Simulation

### Configuration Change
Updated nginx configuration:

listen 127.0.0.1:80;

### Validation
Command executed:

sudo nginx -t  

### Output Observed
- Configuration syntax: **OK**

![Config Validation](../assets/screenshots/day-9/day-9-config-validation.png)

### Action Performed
sudo systemctl restart nginx  

### Interpretation
The service was intentionally restricted to the loopback interface.

---

## Observed Failure

### Commands Executed
curl -I localhost  
curl http://10.0.2.15  

### Output Observed
- Localhost: **working (200 OK)**  
- IP access: **failed (connection refused)**  

### Failure Evidence

![Local vs IP Failure](../assets/screenshots/day-9/day-9-local-vs-ip-comparison.png)

### Interpretation
The service appeared healthy but was not accessible externally via IP.

---

## Root Cause Investigation

### Command Executed
sudo ss -tulpn | grep :80  

### Output Observed
- nginx listening on: **127.0.0.1:80**

### Binding Evidence

![Binding Check](../assets/screenshots/day-9/day-9-binding-localhost.png)

### Root Cause
Nginx was bound only to the loopback interface instead of all network interfaces.

---

## Resolution

### Configuration Restored
listen 80 default_server;  
listen [::]:80 default_server;  

### Commands Executed
sudo nginx -t  
sudo systemctl restart nginx  

### Interpretation
Service binding was restored to allow access from all interfaces.

---

## Validation

### Command Executed
curl http://10.0.2.15  

### Output Observed
- HTTP response successful  
- Service accessible via IP  

### Final Evidence

![Service Restored](../assets/screenshots/day-9/day-9-restored.png)

### Interpretation
Full service accessibility was successfully restored.

---

## Skills Practiced

- Understanding service binding behavior  
- Differentiating localhost vs external access  
- Diagnosing partial service availability issues  
- Using `ss` for port/interface inspection  
- Configuration-level troubleshooting  
- End-to-end validation of service recovery  

---

## Conclusion

This exercise demonstrated a real-world scenario where a service appeared operational but was inaccessible externally due to binding misconfiguration. Systematic troubleshooting identified the root cause and restored full service availability.
