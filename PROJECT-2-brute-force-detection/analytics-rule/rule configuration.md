# Analytics Rule

## Name

Brute Force Detection - Failed Logins

## Description

I created this rule to automatically detect multiple failed login attempts within a short period of time instead of manually running queries.

## Query

SecurityEvent
| where TimeGenerated >= ago(10m)
| where EventID == 4625
| summarize FailedAttempts = count() by IpAddress, Account, LogonType
| where FailedAttempts >= 3

## Configuration

* The rule runs every 5 minutes
* It checks data from the last 10 minutes
* It triggers an alert when there are any matching results

## Outcome

After creating the rule, it successfully generated an alert when I simulated multiple failed login attempts. This confirms that the detection is working automatically in Microsoft Sentinel.

