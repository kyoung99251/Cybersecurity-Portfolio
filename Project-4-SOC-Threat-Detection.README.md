by Project 4: SSH Threat Detection & Incident Response

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

Scope: This was an authorized lab simulation, not an actual security breach . Automatic threshold-based banning was configured but not demonstrated during this test.


Lab Architecture

Environment

The SOC lab was built using Oracle VirtualBox to run an Ubuntu Server virtual machine on a Windows host.

Component	Configuration
Host operating system	Windows
Virtualization	Oracle VirtualBox
Guest operating system	Ubuntu Server
Guest IP address	10.0.2.15
Network mode	NAT
Host SSH port	TCP 2222
Guest SSH port	TCP 22
NAT gateway	10.0.2.2
Security monitoring	OpenSSH logs and Fail2ban

Network Communication

Windows PowerShell was used to initiate SSH connections to the Ubuntu Server through VirtualBox NAT port forwarding.

The host’s TCP port 2222 forwarded incoming connections to TCP port 22 on the Ubuntu virtual machine.

The connection command was:

ssh -p 2222 socanalyst@127.0.0.1

Authentication events on Ubuntu identified the connection source as 10.0.2.2, the VirtualBox NAT gateway.

Security Monitoring

OpenSSH authentication events were examined using the Linux systemd journal.

Fail2ban monitored SSH authentication failures and recorded matching events associated with the NAT gateway address.

The environment was isolated for authorized  testing. Because NAT translated host-originated connections to the gateway address, the source IP observed in the Ubuntu logs represented the VirtualBox networking path rather than a distinct external attacker.

Threat Detection and Log Analysis

Investigation Objective

The objective was to generate controlled SSH authentication failures, identify the source of the activity, and determine whether the security monitoring system detected the events.

Simulated Authentication Failures

From Windows PowerShell, an SSH connection was attempted using a nonexistent account:

ssh -p 2222 fakeuser@127.0.0.1

The unsuccessful authentication attempts generated events on the Ubuntu Server.

Log Investigation

The following commands were used to investigate SSH activity and Fail2ban detection:

sudo journalctl -u ssh -n 20
sudo fail2ban-client status sshd
sudo grep 'Found' /var/log/fail2ban.log | tail -n 10

Evidence Collected

Fail2ban recorded three matching SSH authentication failure events associated with source IP 10.0.2.2.

The logs contained entries matching the following structure:

[sshd] Found 10.0.2.2

The source address was identified as the VirtualBox NAT gateway used by the Windows host to reach the Ubuntu virtual machine.

Detection Findings

* Three SSH authentication failure events were detected.
* The Fail2ban SSH jail was active.
* The configured threshold was five failures within 600 seconds.
* The observed test activity did not trigger an automatic ban.
* Log correlation successfully linked the matching failures to the NAT gateway address.

Security Analysis

Repeated failed authentication attempts can indicate password guessing, brute-force activity, or misconfigured credentials.

In this investigation, the activity was deliberately generated in an authorized lab environment.

The behavior resembles techniques associated with MITRE ATT&CK T1110 (Brute Force), but no real-world attack or successful compromise occurred.

Conclusion

The detection phase confirmed that SSH authentication failures were visible in security logs and that Fail2ban identified matching events.

These findings provided the basis for the subsequent manual containment and recovery tests.