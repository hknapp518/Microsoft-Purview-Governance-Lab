# Data Loss Prevention

## Overview

Microsoft Purview Data Loss Prevention (DLP) helps organizations identify, monitor, and protect sensitive information across Microsoft 365 services. By combining sensitivity labels with built-in Sensitive Information Types (SITs), organizations can prevent unauthorized sharing of regulated data while supporting compliance and reducing business risk.

For the Knapp Healthcare engagement, DLP policies were implemented to protect healthcare, payment card, and financial information stored in Exchange Online, SharePoint Online, and OneDrive.

---

## Objectives

- Prevent unauthorized external sharing of sensitive data
- Protect regulated healthcare and financial information
- Demonstrate both label-based and content-based DLP policies
- Reduce organizational risk through automated policy enforcement
- Support HIPAA and PCI DSS compliance requirements

---

## Policies

| Policy | Detection Method | Purpose |
|---------|------------------|---------|
| Block PHI External Sharing | Sensitivity Label | Prevent external sharing of documents classified as Confidential – PHI Data |
| Block PCI External Sharing | Sensitivity Label | Prevent external sharing of documents classified as Highly Confidential – PCI Data |
| Protect Financial Records | Sensitive Information Types (SITs) | Detect and protect financial information including credit card numbers, bank accounts, IBANs, and SWIFT codes |

---

## Detection Methods

### Sensitivity Labels

The PHI and PCI policies rely on Microsoft Purview Sensitivity Labels applied through the organization's Information Protection strategy. Documents containing regulated healthcare or payment card information inherit protection based on their assigned classification.

### Sensitive Information Types (SITs)

The Financial Records policy demonstrates content inspection using Microsoft Purview's built-in Sensitive Information Types rather than document labels.

Configured detections include:

- Credit Card Number
- U.S. Bank Account Number
- International Bank Account Number (IBAN)
- SWIFT Code

This approach enables automatic protection even when documents have not yet been manually or automatically classified.

---

## Deployment Approach

New DLP policies were initially deployed in **Simulation with Notifications** mode to validate policy matches, review potential false positives, and ensure legitimate business processes were not disrupted.

Following successful validation, policies can be transitioned to **Enforced** mode as part of a phased production rollout.

---

## Business Value

This implementation demonstrates how Microsoft Purview can combine information classification and content inspection to automatically protect sensitive data across Microsoft 365. By leveraging both sensitivity labels and built-in Sensitive Information Types, Knapp Healthcare strengthened governance controls while reducing the risk of accidental disclosure of healthcare, payment card, and financial information.
