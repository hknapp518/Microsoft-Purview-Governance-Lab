# Microsoft Purview Data Security & Governance Lab

## Overview

A Microsoft Purview project focused on identifying, protecting, monitoring, and investigating sensitive data across Microsoft 365.

The project uses fictional healthcare and critical-infrastructure scenarios to test data classification, DLP enforcement, security alerting, and SIEM monitoring.

## Architecture

**Sensitive Data → Microsoft Purview → DLP Enforcement → Microsoft Defender XDR → Azure Event Hubs → Splunk**

## What I Built

### Information Protection
- Sensitivity labels for PHI, PCI, financial, and internal data
- Custom Sensitive Information Types using regex and contextual evidence
- Auto-labeling and classification testing
- Custom BCSI classifier for a NERC CIP-inspired scenario

### Data Loss Prevention
- PHI external-sharing protection
- PCI external-sharing protection
- Financial data protection
- Clinical research identifier protection
- BCSI external-sharing enforcement
- Simulation, policy tips, blocking, and alert generation

### Security Monitoring
- Validated DLP events in Microsoft Defender XDR
- Investigated security telemetry using KQL
- Streamed Defender telemetry through Azure Event Hubs
- Ingested and investigated DLP events in Splunk using SPL

## Featured Test: BCSI External Sharing

For the final use case, I created a custom Sensitive Information Type to identify a fictional BES Cyber System Information (BCSI) identifier using regex and contextual evidence.

The classifier was connected to a DLP policy designed to prevent the information from being shared externally.

The final test demonstrated:

**Custom BCSI SIT → Detection → External Sharing Attempt → Message Blocked → Defender XDR → Azure Event Hubs → Splunk**

## Technologies

`Microsoft Purview` · `Defender XDR` · `Microsoft 365` · `Azure Event Hubs` · `Splunk Enterprise` · `KQL` · `SPL` · `Regex`

## Repository

- **Information-Protection/** — Sensitivity labels, custom SITs, and classification
- **Data-Loss-Prevention/** — DLP policies, enforcement testing, and investigations
- **Event-Hub-Splunk-Integration/** — Defender-to-Splunk integration and validation
- **Lessons-Learned/** — Technical and operational takeaways

## Key Takeaway

Building the policy is only the beginning.
Effective data protection requires continuous testing, tuning, reducing false positives, validating enforcement, and ensuring the resulting security telemetry reaches the teams responsible for investigation.

## Disclaimer

This project was created for educational and portfolio purposes. All organizations, users, identifiers, sensitive data, and security events used for testing are fictional.

The BCSI scenario is NERC CIP-inspired and does not represent or claim compliance with a specific NERC CIP requirement.
