Project 4: SSH Threat Detection & Incident Response

Project Overview

This project demonstrates a controlled Security Operations Center (SOC) investigation using an Ubuntu Server virtual machine, OpenSSH, and Fail2ban.

The objective was to simulate failed SSH authentication attempts, investigate security logs, identify the source IP address, manually contain the simulated threat, and verify that normal access could be restored.

Technologies Used

* Ubuntu Server
* Oracle VirtualBox
* OpenSSH
* Fail2ban
* Linux systemd journal
* Windows PowerShell

Skills Demonstrated

* Linux server administration
* SSH configuration and troubleshooting
* Security log analysis
* Authentication failure investigation
* IP-based containment
* Incident response verification
* Network address translation (NAT) troubleshooting

Investigation Summary

Three failed SSH authentication events were detected and correlated with the source address 10.0.2.2, the VirtualBox NAT gateway.

The address was manually banned through Fail2ban, and the ban was verified in the security logs.

Following containment testing, the ban was removed and SSH connectivity from Windows to Ubuntu was successfully restored.

Outcome: Successfully demonstrated detection, investigation, manual containment, and recovery in a controlled cybersecurity lab environment.

Scope: This was an authorized lab simulation, not an actual security breach. Automatic threshold-based banning was configured but not demonstrated during this test.