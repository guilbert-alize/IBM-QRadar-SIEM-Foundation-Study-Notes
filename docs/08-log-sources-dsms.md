# Log Source Protocols and DSMs

## Overview
This chapter summarizes the **Log Source Protocols and DSMs** course from the IBM QRadar SIEM Foundation learning path. It explains how IBM QRadar SIEM collects and processes events using protocols and Device Support Modules (DSMs). I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Log Source Protocols
QRadar collects events using various protocols:
- **Listening Protocols**: Syslog, TLS Syslog, TCP/UDP Multiline Syslog, Syslog Redirect.
- **Polling Protocols**: JDBC, Log File, SMB Tail.
- **Specialty Protocols**: REST APIs (e.g., AWS CloudTrail, Office 365), SDEE.
- **Example**: Syslog uses TCP/UDP 514; TLS Syslog uses port 6514 with certificates.

## Device Support Modules (DSMs)
- Parse raw event data into normalized fields (e.g., IP, username, event ID).
- Support over 315 log source types, with 174 auto-detectable via Traffic Analysis.
- **DSM Editor**: Customizes parsing for unsupported devices using regex or JSON.

## Traffic Analysis
- Auto-detects log sources from Syslog/SNMP data.
- Assigns unknown events to “SIM Generic-2” until manually configured.
- Determines source/destination IPs from payload, Syslog header, or packet source.

## Key Takeaways
QRadar’s protocols and DSMs enable flexible, accurate event collection and parsing for diverse environments.
