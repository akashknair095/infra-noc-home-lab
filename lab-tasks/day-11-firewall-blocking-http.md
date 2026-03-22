# Firewall Blocking HTTP Access (UFW Simulation)

## Objective

Simulate a scenario where HTTP traffic is blocked by firewall rules despite the web service running normally, and analyze the behavior in a virtualized environment.

---

# Baseline Validation

## Service and Connectivity Check

Command executed:

sudo systemctl status nginx  
curl -I localhost  
curl -I http://10.0.2.15  

## Output Observed

- Nginx service was active (running)
- HTTP response from localhost: 200 OK
- HTTP response from server IP: 200 OK

## Interpretation

The web service was fully operational and accessible both locally and via the system IP address.

---

# Firewall Initialization

## Command Executed

sudo ufw enable  
sudo ufw status  

![UFW Enabled](../assets/screenshots/day-11/day-11-ufw-enabled-clean.png)

## Output Observed

- Firewall status: active
- No rules configured

## Interpretation

Firewall was enabled in a clean state with no filtering rules applied.

---

# Firewall Rule Configuration

## Commands Executed

sudo ufw default deny incoming  
sudo ufw allow ssh  
sudo ufw deny 80  
sudo ufw status  

![UFW Rules Applied](../assets/screenshots/day-11/day-11-ufw-rules-applied.png)

## Output Observed

- Default incoming policy: deny
- Port 22 (SSH): allowed
- Port 80 (HTTP): denied

## Interpretation

The firewall was configured to block HTTP traffic while allowing SSH access.

---

# Connectivity Testing After Firewall Rules

## Commands Executed

curl -I localhost  
curl -I http://10.0.2.15  

![Firewall Test](../assets/screenshots/day-11/day-11-firewall-test.png)

## Output Observed

- Localhost request: 200 OK
- IP-based request: 200 OK

## Interpretation

Despite firewall rules denying port 80, HTTP traffic remained accessible.

---

# Investigation

## Port Verification

Command executed:

sudo ss -tulpn | grep :80  

![Port Verification](../assets/screenshots/day-11/day-11-port-verification.png)

## Output Observed

- Nginx listening on:
  - 0.0.0.0:80
  - [::]:80

## Analysis

- Nginx was correctly bound to all interfaces
- Service was running and accepting connections

---

# Root Cause Analysis

The expected behavior was for HTTP access to be blocked by UFW rules. However, access remained available due to the following reason:

- The testing was performed from within the same virtual machine
- Traffic to `localhost` and the system IP (`10.0.2.15`) did not traverse the firewall as external incoming traffic
- The virtual machine was using NAT networking, which limits simulation of external traffic filtering

---

# Resolution

No changes were required to the firewall configuration.

Understanding of environment behavior was sufficient to explain the observed results.

---

# Skills Practiced

- Firewall configuration using UFW
- Understanding default deny policies
- Differentiating between local and external traffic
- Service validation under firewall rules
- Port inspection using `ss`
- Root cause analysis in virtualized environments

---

# Conclusion

This exercise demonstrated firewall configuration and highlighted the difference between local and external traffic behavior. Although HTTP access was not blocked due to NAT-based virtualization, the scenario provided valuable insight into firewall behavior and network traffic flow in Linux systems.
