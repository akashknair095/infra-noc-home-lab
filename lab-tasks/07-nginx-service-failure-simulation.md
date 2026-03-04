# Nginx Service Failure Simulation

## Objective
Simulate service-level failures and practice troubleshooting techniques to restore application availability.

This exercise includes two scenarios:
1. Service stopped unexpectedly
2. Service failing to start due to configuration error

---

# Scenario 1 — Service Stopped

## Service Verification
Command executed:

sudo systemctl status nginx

Output observed:

Active: active (running)

Service was initially running normally.

---

## Simulated Service Failure

Command executed:

sudo systemctl stop nginx

Verification:

sudo systemctl status nginx

Output observed:

Active: inactive (dead)

---

## Connectivity Test

Command executed:

curl localhost

Result:

curl: (7) Failed to connect to localhost port 80

Interpretation:

The web service became unreachable because nginx was stopped.

---

## Service Restoration

Command executed:

sudo systemctl start nginx

Verification:

sudo systemctl status nginx

Output observed:

Active: active (running)

---

## Application Validation

Command executed:

curl -I localhost

Output observed:

HTTP/1.1 200 OK
Server: nginx/1.24.0

Interpretation:

The web server resumed normal operation.

---

# Scenario 2 — Configuration Failure

## Introduced Configuration Error

Edited file:

/etc/nginx/sites-enabled/default

Added invalid directive:

invalid_directive on;

---

## Configuration Validation

Command executed:

sudo nginx -t

Output observed:

unknown directive "invalid_directive"
/etc/nginx/sites-enabled/default:24
configuration file test failed

Interpretation:

The nginx configuration contained an invalid directive.

---

## Restart Attempt

Command executed:

sudo systemctl restart nginx

Result:

Job for nginx.service failed because the control process exited with error code.

Service status:

Active: failed

Interpretation:

Nginx failed to start due to configuration error.

---

## Root Cause Investigation

Command executed:

sudo journalctl -u nginx --no-pager | tail -20

Logs confirmed the configuration error preventing startup.

---

## Configuration Fix

Removed the invalid directive from the configuration file.

Validation performed:

sudo nginx -t

Output observed:

syntax is ok
test is successful

---

## Service Restoration

Command executed:

sudo systemctl start nginx

Verification:

sudo systemctl status nginx

Output observed:

Active: active (running)

---

## Final Service Validation

Command executed:

curl -I localhost

Output observed:

HTTP/1.1 200 OK
Server: nginx/1.24.0

Interpretation:

The nginx service was successfully restored and began serving HTTP requests again.

---

# Skills Practiced

- Service monitoring using systemctl
- Log analysis using journalctl
- Configuration validation using nginx -t
- Troubleshooting failed service startups
- Identifying configuration errors
- Restoring application availability
- Verifying HTTP responses using curl

---

# Conclusion

This exercise simulated real-world service failures including a stopped service and a configuration error preventing service startup. Structured troubleshooting and validation steps were used to restore service availability.
