# Incident 3 — Service Fails to Start (cron)

## User-Reported Issue
A core background service was not running as expected.

## Validation
Checked service status and confirmed it was not active.

## Diagnosis
The service was administratively masked, preventing it from starting.
Logs showed no crash or binary failure.

## Root Cause
`cron.service` was masked at the systemd level.

## Resolution
Unmasked and restarted the service using systemctl.

## Verification
Confirmed the service is running and enabled to start on boot.

## Lessons Learned
- A masked service cannot start regardless of health
- Always confirm unit state before assuming service failure
- Logs help distinguish misconfiguration from crashes
