Project 1 — Detection Engineering with Microsoft Sentinel

Summary:
This project demonstrates my ability to detect and investigate authentication-based threats using Microsoft Sentinel in a SOC-style workflow. I collected sign-in logs, created a KQL detection query, built an analytics rule, and investigated a real incident involving repeated failed login attempts.

Objective:
This project focused on detecting and investigating suspicious login activity using Microsoft Sentinel. I collected authentication logs, created a detection query with KQL, built an analytics rule, and investigated a real incident.

Tools Used:
Microsoft Sentinel
Microsoft Defender
Microsoft Entra ID (Azure AD)
Kusto Query Language (KQL)
Log Collection
I connected Entra ID sign-in logs to Microsoft Sentinel and confirmed that failed login activity was visible for monitoring.

Detecting Suspicious Activity
I created a KQL query to detect multiple failed login attempts from the same user and IP address, which can indicate brute-force behaviour.

SigninLogs:

| where ResultType != 0
| summarize FailedAttempts=count() by UserPrincipalName, IPAddress
| where FailedAttempts > 5
| sort by FailedAttempts desc
Analytics Rule
I converted the query into a scheduled analytics rule so Microsoft Sentinel could automatically generate incidents when suspicious login activity was detected.

Incident Investigation:
An incident titled “Attempts to sign in to disabled accounts” was generated. Investigation showed repeated failed login attempts against a disabled account, with no successful compromise.

Skills Demonstrated:
Log ingestion in Microsoft Sentinel
KQL detection query writing
Analytics rule creation
Security incident investigation
Understanding brute-force attack behaviour
