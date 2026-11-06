# Windows Security Monitoring & Event Log Analysis

## Project Overview
Hands-on Blue Team investigation of Windows Security logs using Event Viewer.

Windows Security Monitoring & Event Log Analysis

Project Overview

Conducted a hands-on Blue Team investigation using Windows Event Viewer to examine authentication activity, identify failed login causes, and assess potential security concerns.

Environment: Windows local workstation
Tools: Windows Event Viewer, Windows Security Logs
Focus: Security Operations Center (SOC), authentication monitoring, event correlation

Investigation Objectives

* Identify successful and failed authentication events.
* Analyze Windows Event IDs and logon types.
* Interpret authentication failure codes.
* Correlate security events with known user activity.
* Investigate evidence of suspicious authentication patterns.

Investigation Findings

Event ID	Description	Findings
4624	Successful logon	SYSTEM account, Logon Type 5
4625	Failed logon	Interactive login failed because password expired
4625	Failed logon	Interactive login failed because an incorrect password was entered
4720	User account created	No matching events found
4726	User account deleted	No matching events found
4740	Account lockout	No matching events found

Authentication Failure Analysis

Finding 1: Expired Password

* Event ID: 4625
* Account: Owner
* Logon Type: 2 (Interactive)
* Failure Reason: Password expired
* Analysis: Event timestamp matched a known period of computer login difficulties.
* Assessment: Likely legitimate authentication issue.

Finding 2: Incorrect Password

* Date: November 5, 2026
* Event ID: 4625
* Account: Owner
* Logon Type: 2 (Interactive)
* Status: 0xC000006D
* Sub Status: 0xC000006A
* Analysis: Windows rejected an incorrect password for the account.
* Assessment: Likely user error; not independently confirmed.

Finding 3: Successful Service Logon

* Event ID: 4624
* Account: SYSTEM
* Logon Type: 5
* Analysis: Successful Windows service authentication.
* Assessment: Consistent with normal operating system activity.

Security Assessment

The reviewed authentication failures were separated by days rather than occurring in a rapid sequence. No obvious brute-force pattern was identified in the events examined.

No matching account creation, account deletion, or account lockout events were found in the available Security log.

These findings do not establish that the workstation is free of threats; they reflect the limited events reviewed.

Conclusion

This investigation demonstrated practical Windows security monitoring, authentication troubleshooting, event correlation, and preliminary incident triage.

Skills demonstrated: Windows Event Viewer, Security Event Analysis, Authentication Monitoring, Log Interpretation, SOC Investigation, Security Documentation.

Evidence

Redacted screenshots of the relevant Windows Security events will be stored in the Screenshots folder.