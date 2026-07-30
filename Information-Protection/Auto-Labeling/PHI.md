# Auto-Label PHI

## Overview

The **Auto-Label PHI** policy automatically identifies protected health information (PHI) within Microsoft 365 content and applies the **Confidential – PHI Data** sensitivity label.

Rather than relying on users to manually classify documents, Microsoft Purview inspects content for healthcare-related Sensitive Information Types (SITs) and automatically classifies qualifying files and emails.

This automated classification serves as the foundation for downstream Information Protection and Data Loss Prevention (DLP) policies.

---

## Business Scenario

Following a governance assessment at Knapp Healthcare, it was determined that employees were manually handling documents containing protected health information. This created the risk of inconsistent classification and accidental disclosure.

To improve consistency and reduce reliance on manual labeling, an Auto-Labeling policy was implemented to automatically classify healthcare-related content whenever regulated information was detected.

---

## Policy Configuration

| Setting | Value |
|---------|-------|
| Policy Name | Auto-Label PHI |
| Label Applied | Confidential – PHI Data |
| Mode | On |
| Locations | Exchange Online, SharePoint Online, OneDrive |

---

## Detection Criteria

The policy uses Microsoft Purview built-in Sensitive Information Types including:

- Brand Medication Names
- Generic Medication Names
- Types of Medication
- Medicare Beneficiary Identifier (MBI)
- U.S. Individual Taxpayer Identification Number (ITIN)
- U.S. Social Security Number (SSN)

When one or more configured Sensitive Information Types are detected, Microsoft Purview automatically applies the **Confidential – PHI Data** sensitivity label.

---

## Integration with DLP

Once the sensitivity label has been automatically applied, downstream Microsoft Purview DLP policies use the label as a condition to:

- Block unauthorized external sharing
- Protect healthcare information stored in Microsoft 365
- Generate audit events
- Notify users of policy violations

This approach separates **classification** from **enforcement**, making security controls easier to manage and maintain.

---

## Business Value

Automatically classifying protected health information improves data governance by ensuring sensitive healthcare records receive consistent protection regardless of who creates or stores the content.

By combining Auto-Labeling with Microsoft Purview DLP, Knapp Healthcare reduced the likelihood of human error while strengthening HIPAA compliance and improving the organization's overall data protection posture.<img width="588" height="836" alt="image" src="https://github.com/user-attachments/assets/64e4d0a0-9592-462b-870c-90d58c3e378a" />
