# QRadar SIEM Functional Architecture

## Overview
This chapter summarizes the **QRadar SIEM Functional Architecture** course from the IBM QRadar SIEM Foundation learning path. It covers the modular and scalable architecture of IBM QRadar SIEM, designed to process large volumes of security data efficiently. I used **Grok**, created by xAI, to refine my notes for clarity and technical accuracy.

## QRadar Architecture Components
QRadar’s architecture consists of modular components for event and flow processing:

- **Event Processing**:
  - **Event Collectors (15xx)**: Normalize raw log data, enforce license limits, and perform traffic analysis to identify log sources.
  - **Event Processors (16xx)**: Correlate events, apply rules, and store data in the Ariel database.
  - **Console (31xx)**: Hosts the Magistrate for offense generation and global rule evaluation.

- **Flow Processing**:
  - **Flow Collectors**: Capture network flow data (e.g., source/destination IPs, ports, protocols).
  - **Flow Processors (17xx)**: Analyze flows for patterns, such as beaconing or encrypted traffic.
  - **QFlow/QNI**: Inspects packet payloads (first 64 bytes or full) to extract metadata (e.g., hashes, user IDs).

- **Combined Appliances (18xx)**: Integrate event and flow processing for smaller deployments.

## Event Pipeline
The QRadar event pipeline ensures efficient data handling:
1. **Collection**: Events are gathered via protocols (e.g., Syslog, JDBC) and normalized using Device Support Modules (DSMs).
2. **Coalescing**: Combines duplicate events within a 10-second window to optimize storage.
3. **Rule Evaluation**: The Custom Rule Engine (CRE) applies ~750 predefined rules to detect offenses.
4. **Storage**: Events and flows are stored in the Ariel database for searches and reporting.
5. **Offense Generation**: The Magistrate correlates data to create actionable offenses.

## Deployment Models
QRadar supports flexible deployments:
- **On-Premises**: Physical or virtual appliances (e.g., 31xx Console).
- **Cloud (QRoC)**: QRadar on Cloud with Data Gateway for secure log transmission.
- **Hybrid**: Combines on-premises and cloud components.
- **High Availability (HA) and Disaster Recovery (DR)**: Ensures redundancy with clustered appliances and data replication.

## Key Takeaways
QRadar’s architecture enables scalable, real-time threat detection through modular components and an efficient event pipeline, making it ideal for enterprise and cloud environments.
