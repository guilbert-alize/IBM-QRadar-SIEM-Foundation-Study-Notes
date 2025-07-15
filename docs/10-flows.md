# QRadar Flows

## Overview
This chapter covers the concepts of flows in IBM QRadar SIEM, based on the IBM QRadar SIEM Foundation learning path. It explains the differences between events and flows, types of flow data, and their use in network analysis and anomaly detection. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Events vs. Flows
- **Events**:
  - Represent a moment in time (e.g., a user’s unsuccessful login attempt on a firewall).
  - Visible in the **Log Activity** tab.
  - Example: A login attempt recorded as a single event.

- **Flows**:
  - Represent network activity with duration (e.g., an employee sending an email, visiting a webpage, or downloading a file).
  - Visible in the **Network Activity** tab.
  - Normalize IP addresses, ports, byte/packet counts into sessions between two hosts.
  - Capture raw network traffic, providing a snapshot of communication.

## Flow Types
QRadar collects various flow types, each providing different levels of metadata from TCP/IP headers:
- **NetFlow, IPFIX, JFlow, sFlow**: Provide metadata like byte count, duration, source/destination IPs, and ports.
- **Cisco NetFlow**: Captures basic network flow data.
- **QRadar QFlow**: Inspects the first 64 bytes of packet payloads to identify applications (e.g., Facebook via UTF8 payload search).
- **QRadar Network Insights (QNI)**: Analyzes full payloads to extract detailed metadata (e.g., URLs, file hashes, HTTP referrers) for deeper insights.

## Flow Analysis
QRadar uses flows to analyze network activity and detect anomalies:
- **NetFlow**: Focuses on network activity metrics (e.g., port 53 for DNS, port 80 for web traffic, byte counts). Useful for detecting scanning (e.g., FTP logs).
- **QFlow**: Inspects 64 bytes of payload to identify applications (e.g., `SELECT UTF8(destinationpayload) as rawpayload FROM flows WHERE rawpayload LIKE '%facebook%'`). Uses app detection algorithms and state-based decoding to identify protocols.
- **QNI**: Provides advanced details like requested URLs (e.g., Twitter), file hashes, and categories. Detects malicious activity by checking file hashes against threat intelligence.

## Anomaly Detection
- **QFlow Analysis**:
  - Detects anomalies using packet headers (e.g., source IP, byte counts) and payload signatures.
  - Identifies malicious ports (e.g., peer-to-peer traffic) or protocols (e.g., ICMP mapping).
  - Example: Detects BitTorrent activity based on high flow counts (e.g., 100+ flows) or SSH anomalies on non-standard ports (e.g., 992).

- **Rules**: Predefined rules trigger offenses for anomalies (e.g., P2P application with high flow count, unexpected SSH connections).

## Flow Collection Commands
Example commands to send flow data to QRadar:
- Basic NetFlow:
  ```bash
  nprobe /c --collector 172.16.60.10:2055 --interface c:\Lx\Flows\flow_tests3.pcap --verbose 2 --flow-version 5
