# Attack Simulation

## What I Did

To generate failed login events, I used my Windows virtual machine.

I locked the system and then attempted to log in multiple times using incorrect passwords.

## Steps

1. Opened the Windows VM
2. Locked the system using Win + L
3. Entered the wrong password several times
4. Repeated this process to generate multiple failed login attempts

## Result

This created Event ID 4625 logs in Microsoft Sentinel, which were then used for detection and analysis.

