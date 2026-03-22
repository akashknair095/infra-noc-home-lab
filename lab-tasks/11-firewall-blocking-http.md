# Firewall Blocking HTTP Access (UFW)

## Objective

Simulate a scenario where firewall rules restrict HTTP access to a running nginx service.

---

# Baseline Verification

## Network Verification

Command executed:

ip a

![Network Baseline](../assets/screenshots/day-11/day-11-network-baseline.png)

Output observed:

System has an active IP address (e.g., 10.0.2.15)

---

## Service Status

Command executed:

sudo systemctl status nginx

![Service Running](../assets/screenshots/day-11/day-11-service-baseline.png)

Output observed:

Active: active (running)

---

## Port Verification

Command executed:

sudo ss -tulpn | grep :80

![Port Listening](../assets/screenshots/day-11/day-11-port-verification.png)

Output observed:

nginx listening on 0.0.0.0:80

---

## Connectivity Test

Command executed:

curl -I localhost  
curl -I http://10.0.2.15  

![Baseline Connectivity](../assets/screenshots/day-11/day-11-firewall-test.png)

Output observed:

HTTP/1.1 200 OK

Interpretation:

The service is accessible both locally and via IP address.

---

# Simulated Firewall Restriction

## Enable Firewall

Command executed:

sudo ufw enable  
sudo ufw status  

![UFW Enabled](../assets/screenshots/day-11/day-11-ufw-enabled-clean.png)

---

## Apply Blocking Rules

Command executed:

sudo ufw default deny incoming  
sudo ufw allow ssh  
sudo ufw deny 80  
sudo ufw status  

![UFW Rules](../assets/screenshots/day-11/day-11-ufw-rules-applied.png)

Output observed:

80 DENY Anywhere

---

# Connectivity Test After Firewall Rules

Command executed:

curl -I localhost  
curl -I http://10.0.2.15  

![Post Firewall Test](../assets/screenshots/day-11/day-11-firewall-test.png)

Output observed:

HTTP/1.1 200 OK

---

## Observation

Despite firewall rules denying port 80, the service remains accessible.

---

## Explanation

The test was performed from the same host (local machine).  
Traffic originating from the same system does not pass through the firewall as external incoming traffic.

As a result:

- UFW rules do not block this request
- The request is treated as internal/local traffic

---

## Real-World Behavior

In a production environment:

- Requests from external systems would be blocked ❌  
- Firewall rules would correctly deny HTTP access  

---

# Resolution

## Allow HTTP Traffic

Command executed:

sudo ufw allow 80  
sudo ufw status  

---

## Final Validation

Command executed:

curl -I http://10.0.2.15  

Output observed:

HTTP/1.1 200 OK

Interpretation:

HTTP access confirmed after allowing port 80.

---

# Skills Practiced

- Firewall configuration using UFW  
- Understanding local vs external traffic behavior  
- Identifying environment-based limitations  
- Service validation using curl  
- Network troubleshooting fundamentals  

---

# Conclusion

This exercise demonstrated how firewall rules can restrict service access.  
It also highlighted an important limitation when testing within a local environment, where firewall rules may not affect internal traffic.  

Understanding this distinction is critical for accurate troubleshooting in real-world scenarios.
