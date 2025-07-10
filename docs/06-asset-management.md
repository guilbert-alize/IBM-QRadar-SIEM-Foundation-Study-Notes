# Asset Management

## Overview
This chapter summarizes the **Asset Management** course from the IBM QRadar SIEM Foundation learning path. It covers how IBM QRadar SIEM builds and manages asset profiles for network endpoints. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Asset Management
Assets are network endpoints (e.g., servers, devices) that send/receive data. QRadar creates **asset profiles** to track behavior and vulnerabilities.

- **Data Sources**:
  - **Events**: Provide identity data (e.g., usernames, MAC addresses) from logs like DHCP or authentication servers.
  - **Flows**: Capture bidirectional traffic (e.g., IPs, ports, protocols).
  - **Vulnerability Scanners**: Supply OS, software, and patch details.
  - **User Input**: Manual updates to the asset database.

- **Asset Reconciliation**:
  - Correlates data to update profiles, prioritizing identifiers (MAC > NetBIOS > DNS > IP).
  - Merges assets if identifiers match to avoid duplication.

- **Deviant Asset Growth**:
  - Notifications for excessive updates.
  - Mitigated by DSM updates, identity exclusions, or reference set blacklists.

- **Server Discovery**:
  - Uses port signatures (e.g., port 80 for web servers) to categorize assets and reduce false positives.

## Key Takeaways
QRadar’s asset management ensures accurate tracking of network endpoints, supporting vulnerability and threat detection.
