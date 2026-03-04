# SOC Lab: SSH Brute Force Detection using Splunk

## Overview
This lab simulates an SSH brute force attack on a Linux system and detects it using Splunk SIEM.

The goal of this project is to demonstrate how security analysts detect authentication attacks by monitoring Linux log files and building detection queries in Splunk.

## Lab Environment
- Ubuntu Linux VM
- Splunk Enterprise SIEM
- SSH authentication logs
- Attack simulation using SSH

## Log Source
Linux authentication logs:

/var/log/auth.log


These logs contain information about login attempts and failed passwords.

## Attack Simulation
To simulate a brute-force attack, multiple SSH login attempts were made using a fake user.

Command used:

ssh fakeuser@localhost

Multiple incorrect passwords were entered to generate failed login events.

## Detection Query (Splunk SPL)

index=main "Failed password"
| stats count by host
| where count > 5

## Detection Result
Splunk successfully detected the brute-force activity and displayed the number of failed login attempts.

Example result:

host: ubuntu-soc  
failed attempts: 9

## Skills Demonstrated

- SIEM log ingestion
- Linux authentication log analysis
- SSH attack simulation
- Security monitoring with Splunk
- Detection engineering using SPL queries

## Detection Screenshot
![Splunk Detection](screenshot_splunk)
