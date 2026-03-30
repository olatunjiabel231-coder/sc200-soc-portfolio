# Microsoft Sentinel SOC Lab – RDP Brute Force Detection & Investigation

## 🧠 Overview

This project is about detecting and investigating a brute force attack on a Windows Server using Microsoft Sentinel.

The idea is to monitor login activity and identify a situation where multiple failed login attempts are followed by a successful Remote Desktop (RDP) login within a short period of time.

---

## 🎯 Objective

The goal of this project is to:

- Simulate a brute force attack on a Windows Server  
- Build a detection rule using KQL  
- Detect multiple failed logins followed by a successful RDP login  
- Do all of this within a 30-minute window  

---

## 🏗️ Lab Architecture

The environment was set up like this:

Windows Server  
↓  
Azure Arc  
↓  
Azure Monitor Agent  
↓  
Data Collection Rule (DCR)  
↓  
Log Analytics Workspace  
↓  
Microsoft Sentinel  

This setup allows logs from the Windows Server to be collected and analyzed inside Sentinel.

---

## ⚔️ Attack Simulation

To simulate the attack:

- I connected to the Windows Server using RDP  
- I intentionally entered the wrong password multiple times  
- After several failed attempts, I entered the correct password  
- Then I successfully logged into the system  

At first, I didn’t realize that how I handled the RDP session would affect the logs, which later caused some confusion during detection.

---

## 📊 Logs Observed

During the simulation, the following logs were generated:

- Event ID 4625 → Failed login attempts  
- Event ID 4624 → Successful login  
- LogonType 3 → Network authentication attempts  
- LogonType 10 → Actual RDP login session  

Initially, I thought RDP would always show LogonType 10, but I later discovered that failed attempts were showing as LogonType 3 instead.

---

## 🔍 Detection Logic

The detection rule is designed to catch:

- Multiple failed login attempts  
- Followed by a successful RDP login  
- Within 30 minutes  

### Threshold used:

- 10 or more failed attempts  
- At least 1 successful login  

---

## 🧾 KQL Query

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
