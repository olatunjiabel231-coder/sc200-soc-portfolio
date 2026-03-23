# Project 2: Brute Force Detection & Analysis

## Overview

In this project, I simulated multiple failed login attempts on a Windows machine and used Microsoft Sentinel to detect and investigate the activity.

The goal was to determine whether the behavior represented a real brute force attack or normal user activity.

---

## What Happened

I intentionally entered incorrect passwords multiple times while trying to unlock my Windows VM.
This generated several failed login events (Event ID 4625), which were then ingested into Microsoft Sentinel.

---

## How I Detected It

I used the following KQL query to identify accounts with repeated failed login attempts:

```kql
SecurityEvent
| where TimeGenerated >= ago(10m)
| where EventID == 4625
| summarize FailedAttempts = count() by IpAddress, Account, LogonType
| where FailedAttempts >= 3
| sort by FailedAttempts desc
```

This query highlights suspicious login patterns within a short time window.

---

## What I Found

The results showed:

* Multiple failed attempts on the Administrator account
* Source IP was 127.0.0.1 (local machine)
* Logon Type was 7 (workstation unlock)

---

## Analysis

At first glance, this appeared to be a brute force attack. However, further analysis showed that:

* The activity originated from the local machine
* The logon type indicates a workstation unlock attempt

This suggests the behavior was caused by repeated incorrect password entry rather than an external attacker.

---

## Conclusion

This was a false positive scenario, not a real brute force attack.

The project demonstrates the importance of analyzing context before classifying an event as malicious.

---

## Tools Used

* Microsoft Sentinel
* Log Analytics Workspace
* Windows Security Logs

---

## Evidence

Relevant logs and query results are included in the screenshots folder.

