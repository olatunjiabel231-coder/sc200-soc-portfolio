# Attack Simulation

## Overview
In this project, I simulated a brute force attack on a Windows Server using RDP.

## Steps Taken

1. Connected to the Windows Server via RDP
2. Entered incorrect passwords multiple times
3. Generated multiple failed login attempts
4. After several failures, entered the correct password
5. Successfully logged in via RDP

## Logs Generated

- Event ID 4625 → Failed login attempts
- Event ID 4624 → Successful login
- Logon Type 3 → Network authentication attempts
- Logon Type 10 → RDP login

## Outcome
This simulation generated logs that were later used to detect brute force activity using Microsoft Sentinel.
