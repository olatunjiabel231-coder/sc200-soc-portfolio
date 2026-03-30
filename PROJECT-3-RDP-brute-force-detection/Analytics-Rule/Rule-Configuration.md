# Analytics Rule Configuration

## Rule Name
RDP Brute Force Detection

## Description
This rule detects multiple failed login attempts followed by a successful RDP login within a short timeframe.

## Data Source
- Windows Security Events (SecurityEvent table)

## Detection Logic
The rule looks for:
- Multiple failed login attempts (Event ID 4625)
- Followed by a successful login (Event ID 4624)
- Logon Type 10 (RDP)
- Within a 30-minute window

## Threshold
- Failed Attempts >= 10
- At least 1 successful login

## Query Used

```kql
SecurityEvent
| where TimeGenerated >= ago(30m)
| where EventID in (4624, 4625)
| where LogonType in (3, 10)
| extend Account = tolower(Account)
| summarize 
    FailedAttempts = countif(EventID == 4625),
    SuccessfulAttempts = countif(EventID == 4624 and LogonType == 10)
    by Account, IpAddress, bin(TimeGenerated, 30m)
| where FailedAttempts >= 10 and SuccessfulAttempts >= 1
| sort by FailedAttempts desc
```
