# Search and Analytics

## Overview
This chapter summarizes the **Search and Analytics** course from the IBM QRadar SIEM Foundation learning path. It covers IBM QRadar SIEM’s search capabilities for efficient investigations. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Search Capabilities
QRadar provides robust tools for analyzing events and flows:

- **Quick Filters**:
  - Fast searches in Log Activity and Network Activity tabs.
  - Supports operators (e.g., AND, OR, regex) for filtering.

- **Ariel Query Language (AQL)**:
  - SQL-like queries for precise searches (e.g., `SELECT * FROM events WHERE sourceIP='192.168.1.1'`).
  - Enables detailed investigations of user activity or specific events.

- **Indexing**:
  - Speeds up searches by indexing fields (e.g., source IP, payload).
  - Default retention is 30 days (min 1 day, max 2 years).

- **Use Cases**:
  - Identify top applications.
  - Detect specific payloads (e.g., “firewall accept”).
  - Analyze user activity over time.

## Key Takeaways
QRadar’s search and analytics tools enable rapid, precise investigations, critical for threat detection and response.
