# Incident 1 — User Permission Issue (Home Directory)

## User-Reported Issue
The user reported that they could log in successfully but were unable to create or modify files in their home directory. Attempts to create files resulted in a "Permission denied" error.

---

## Validation (User Perspective)
- Switched to the affected user account (`testuser`)
- Attempted to create a file in the home directory
- Confirmed the error occurred as reported

See screenshot: ![User permission denied](../screenshots/01-user-permission-denied.png.png)


---

## Diagnosis
- Inspected permissions on the user's home directory
- Confirmed the directory existed and was owned by the correct user
- Identified that write permissions were missing on `/home/testuser`

See screenshot:[View screenshot](../screenshots/01-user-permission-denied.png)


---

## Root Cause
Home directory permissions for `testuser` were misconfigured, removing write access while still allowing login and directory access.

---

## Resolution
- Restored secure owner-only permissions on the user's home directory using `chmod 700`
- No ownership or additional permission changes were required

See screenshot: [View screenshot](../screenshots/01-user-permission-denied.png)


---

## Verification
- Switched back to the affected user
- Successfully created files in the home directory
- Confirmed normal user functionality was restored

See screenshot: [View screenshot](../screenshots/01-user-permission-denied.png)


---

## Lessons Learned
- Users may be able to log in even when file permissions prevent normal work
- Always reproduce issues as the affected user before diagnosing
- Minimal permission changes reduce risk and simplify troubleshooting
- Verification from the user perspective is critical before closing incidents

