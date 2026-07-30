# Microsoft Purview Governance Lab

## Overview

This project demonstrates a hands-on implementation of Microsoft Purview within a simulated healthcare environment. Using a fictional organization, Knapp Healthcare, I implemented Microsoft Purview to classify sensitive information, automatically apply sensitivity labels, and prevent unauthorized sharing of regulated and proprietary data across Microsoft 365.

---

## Technologies

- Microsoft Purview
- Microsoft 365
- Microsoft Exchange Online
- Microsoft SharePoint Online
- Microsoft OneDrive
- Microsoft Entra ID

---

## Features Implemented

### Information Classification

- Created and published Microsoft Purview Sensitivity Labels
- Configured Built-in Sensitive Information Types
- Developed a Custom Sensitive Information Type using Regular Expressions (Regex)
- Implemented Auto-Labeling policies for:
  - Protected Health Information (PHI)
  - Personally Identifiable Information (PII)
  - Financial Data
  - Payment Card Information (PCI)

### Information Protection

Configured Sensitivity Labels for:

- Public
- Internal Information
- Information Approved for Public Release
- Personal (PII)
- Confidential – Financial Data
- Confidential – PHI Data
- Highly Confidential – PCI Data

### Data Loss Prevention (DLP)

Implemented Microsoft Purview DLP policies to:

- Block PHI External Sharing
- Block PCI External Sharing
- Protect Financial Records
- Protect Clinical Research Protocols

Policies were deployed using Simulation Mode to validate detections before enforcement.

### Custom Detection

Created a Custom Sensitive Information Type using a regular expression to detect proprietary clinical research protocol identifiers.

Example:

```text
KNAPP-PROT-2026-001
```

The custom detector was integrated into a DLP policy to automatically protect organization-specific intellectual property.

---

## Skills Demonstrated

- Microsoft Purview
- Information Protection
- Data Loss Prevention (DLP)
- Sensitivity Labels
- Auto-Labeling
- Sensitive Information Types
- Custom Sensitive Information Types
- Regular Expressions (Regex)
- Microsoft 365 Security
- Data Classification
- HIPAA Security Concepts
- PCI Data Protection

---

## Disclaimer

This project was created for educational and portfolio purposes.

Knapp Healthcare is a fictional organization used to demonstrate Microsoft Purview information protection and compliance capabilities within a realistic enterprise scenario.
