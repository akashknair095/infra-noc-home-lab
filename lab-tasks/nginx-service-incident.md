# Incident Simulation – Nginx Service Outage

## Incident Summary
The Nginx web service was intentionally stopped to simulate a service outage scenario.

---

## Detection
- `systemctl status nginx` showed: inactive (dead)
- `curl localhost` returned no response
- Port 80 was not listening

---

## Impact
Web service unavailable locally.
HTTP requests failed.

---

## Investigation
Verified service status using systemctl.
Checked listening ports using ss.
Reviewed logs using:
sudo journalctl -u nginx --no-pager

No configuration errors found.

---

## Root Cause
Nginx service was stopped manually (simulated failure).

---

## Resolution
Executed:
sudo systemctl start nginx

Verified service restoration:
- systemctl status → active (running)
- curl localhost → Welcome page displayed

---

## Preventive Consideration
In production, monitoring tools should:
- Trigger alert if service becomes inactive
- Monitor port 80 health
- Perform automated restart if configured
