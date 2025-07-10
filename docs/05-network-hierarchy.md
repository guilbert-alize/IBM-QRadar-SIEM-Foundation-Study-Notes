# Network Hierarchy

## Overview
This chapter summarizes the **Network Hierarchy** course from the IBM QRadar SIEM Foundation learning path. It explains how IBM QRadar SIEM organizes network activity for monitoring and rule creation. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Network Hierarchy
- **Definition**: Groups IP addresses or CIDR ranges into logical objects (e.g., by department or location). Does not need to match physical topology.
- **Purpose**:
  - Distinguishes local vs. remote traffic.
  - Detects unauthorized subnets.
  - Supports precise rule creation for threat detection.
- **Management**:
  - Configured via the Admin Console.
  - Automated updates via RESTful APIs (e.g., using Infoblox).
  - Triggered by detecting remote-to-remote (R2R) traffic.
- **Example**: Define a CIDR range (e.g., 192.168.0.0/16) for the finance department to monitor specific behaviors.

## Key Takeaways
QRadar’s network hierarchy enables efficient monitoring and targeted rule application, enhancing security visibility.
