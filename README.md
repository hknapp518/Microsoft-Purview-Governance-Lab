# Microsoft Purview Data Security & Governance Lab

## Overview

A Microsoft Purview project demonstrating how sensitive data can be identified, protected, monitored, and investigated across Microsoft 365 and Splunk.

The project uses fictional healthcare and critical-infrastructure scenarios to build and validate data protection controls from classification through SIEM monitoring.

## Architecture

**Sensitive Data → Microsoft Purview → DLP Enforcement → Microsoft Defender XDR → Azure Event Hubs → Splunk**

## What I Built

### Information Protection
- Sensitivity label taxonomy for PHI, PCI, financial, and internal data
- Custom Sensitive Information Types using regex and contextual evidence
- Custom BCSI classifier for a NERC CIP-inspired information protection scenario
- Auto-labeling and classification testing

### Data Loss Prevention
- PHI external-sharing protection
- PCI external-sharing protection
- Financial data protection
- Custom clinical research identifier protection
- BCSI external-sharing enforcement
- Simulation, policy tips, blocking, and alert generation

### Security Monitoring & SIEM Integration
- Validated DLP alerts in Microsoft Defender XDR
- Investigated security telemetry using KQL
- Streamed Defender telemetry through Azure Event Hub
- Ingested and investigated DLP events in Splunk using SPL

## Featured End-to-End Test: BCSI External Sharing

A custom Sensitive Information Type was created to identify a fictional BES Cyber System Information (BCSI) identifier using regex, supporting keywords, and proximity-based matching.

The classifier was connected to a DLP policy designed to prevent BCSI from being shared externally.

The final test successfully demonstrated:

**Custom BCSI SIT → High-Confidence Detection → External Sharing Attempt → Message Blocked → Defender Alert → Azure Event Hubs → Splunk**

This demonstrates how organization-specific data classification can be connected to prevention and downstream SOC monitoring.

## Technologies

`Microsoft Purview` · `Defender XDR` · `Microsoft 365` · `Azure Event Hubs` · `Splunk Enterprise` · `KQL` · `SPL` · `Regex`

## Repository

- **Information-Protection/** — Sensitivity labels, custom SITs, and classification
- **Data-Loss-Prevention/** — DLP policies, enforcement testing, and investigations
- **Event-Hub-Splunk-Integration/** — Defender-to-Splunk architecture and validation
- **Lessons-Learned/** — Key technical and operational takeaways

## Key Takeaway

The project demonstrates a complete data-security workflow:

**Identify → Classify → Protect → Alert → Stream → Investigate**

Rather than treating Microsoft Purview as an isolated compliance tool, the lab connects information protection and DLP controls directly to security operations and SIEM monitoring.

## Disclaimer

This project was created for educational and portfolio purposes. All organizations, users, identifiers, sensitive data, and security events used in testing are fictional.

The BCSI scenario is a NERC CIP-inspired lab use case and does not represent or claim compliance with a specific NERC CIP requirement.
