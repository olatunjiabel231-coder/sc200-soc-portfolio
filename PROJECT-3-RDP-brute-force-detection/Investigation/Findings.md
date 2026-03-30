# Investigation Findings

## Summary
An incident was generated after detecting multiple failed login attempts followed by a successful RDP login.

## Key Observations

- High number of failed login attempts from the same IP
- Successful login occurred after the failed attempts
- Same account was targeted (Administrator)
- Activity occurred within a short timeframe

## Incident Details

- Severity: High
- Alerts: Multiple alerts generated
- Status: Active

## Entities Identified

- Account: Administrator
- IP Address: Detected source of attack

## Conclusion

This activity is consistent with a brute force attack where an attacker attempts multiple passwords and eventually gains access.
