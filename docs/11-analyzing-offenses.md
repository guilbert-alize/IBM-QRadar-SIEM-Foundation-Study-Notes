# QRadar Foundations - Analyzing Offenses

## Overview
This chapter covers the **QRadar Foundations - Analyzing Offenses** course from the IBM QRadar SIEM Foundation learning path. It explains how IBM QRadar SIEM represents offenses, their management, and the use of the QRadar Analyst Workflow App. It also includes data retention and data obfuscation concepts. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## Offenses
- **Definition**: Alerts to suspicious activity, linking to information for investigation. Treated as security incidents for analyst review.
- **Creation**: QRadar creates offenses when events, flows, or both meet conditions in customizable rules, analyzing:
  - Incoming events and flows.
  - Asset information.
  - Known vulnerabilities.
- **Magistrate Component**: Runs on the Console appliance, maintains offenses, and assigns a **magnitude rating** (1–10, 1 low, 10 high) based on:
  - **Credibility (20%)**: Integrity of the offense, based on log source credibility and multiple sources reporting the same event.
  - **Relevance (50%)**: Impact on the network.
  - **Severity (30%)**: Threat level relative to the destination’s preparedness.
- **Magnitude Calculation**: Considers event/flow count, log sources, offense age, asset weight, vulnerabilities, and threat assessments. Event magnitude can influence offense magnitude via rule actions, but QRadar algorithms control the final rating.

## Offense Chaining
- **Purpose**: Chains related offenses to reduce the number to review, helping identify root causes by connecting symptoms into a single offense.
- **Mechanism**: Uses the **offense index field** (e.g., source IP) to group events/flows from different rules into one offense.
  - Example: An offense with one source IP and multiple destination IPs indicates a single attacker targeting multiple victims.
  - Configurable using normalized fields (e.g., username, source IP) or custom event/flow properties.
- **Identification**: Chained offenses are marked by “preceded by” in the Insights field on the Offense Summary page.

## Offense State and Retention
- **States**:
  - **Active**: Newly created, up to 2500 active offenses maintained.
  - **Dormant**: No events/flows for 30 minutes.
  - **Recalled**: Receives new events/flows, up to 500 recalled offenses.
  - **Inactive**: Closed by a user, no events/flows for 5 days, or after a QRadar upgrade. New events/flows for an inactive offense create a new offense.
- **Retention**: Inactive/closed offenses are kept for a default of 30 days (configurable). Unprotected offenses are removed after the retention period. Flagging prevents deletion.
- **Closing Reasons**: False Positive, Non-Issue, Policy Violation, etc.

## Analyst Workflow App
- Provides a streamlined interface to navigate offense details, investigate incidents, and manage the offense lifecycle.

## Reference Data Collections
- **Purpose**: Store and manage data (business or external) to correlate with events/flows in searches, filters, rules, and responses.
- **Types**:
  - **Reference Set**: One-dimensional list (e.g., IP addresses, user IDs). Example: List of terminated employee IDs to block logins.
  - **Reference Map**: Key-value pairs (e.g., email to user). Example: Map hostnames to users.
  - **Reference Map of Sets**: Key with a list of values (e.g., user with associated IPs).
  - **Reference Map of Maps/Reference Table**: Three-dimensional data (outer-key > inner-key > value). Example: User to action to timestamp.
- **Use Cases**:
  - Integrate third-party threat intelligence (e.g., IBM X-Force for IPs, URLs, MD5 hashes).
  - Create blacklists/whitelists (e.g., allow specific IPs for functions).
- **Management**: Configured via QRadar UI, CLI, RESTful API, or used in AQL queries and rule conditions/responses.

## Data Retention
- **Retention Buckets**: Define how long QRadar retains event/flow data (default: 30 days).
  - Up to 10 buckets for shared data and 10 per tenant.
  - Prioritized from top to bottom; data is stored in the first matching bucket.
  - Tenant-specific data uses tenant buckets; otherwise, it goes to the default bucket.
- **Process**: Events/flows are matched against bucket filters and stored until the deletion policy period expires.
- **Configuration**: Via Admin Console > Admin tab. Modifications apply only to new data.

## Data Obfuscation
- **Purpose**: Protects sensitive data (e.g., usernames, credit card numbers, Social Security numbers) by hiding it from unauthorized users.
- **Process**: Configure data obfuscation profiles in QRadar 7.3.2 to hide custom/normalized properties or payload content.
- **Configuration Steps**:
  - Go to Admin > Data Sources > Data Obfuscation Management.
  - Select a profile, click View Content.
  - Click Add, enter a unique name and description, enable the profile, and define fields or regex for obfuscation.
  - Save the profile.
- **Domains**: Enabled in multi-tenant environments to restrict data visibility based on input sources.

## Key Takeaways
QRadar’s offense analysis, supported by the Analyst Workflow App, reference data, retention buckets, and data obfuscation, enables prioritized incident investigation, efficient data management, and protection of sensitive information.
