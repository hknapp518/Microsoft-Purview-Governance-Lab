# PHI Auto-Labeling

## Overview

This auto-labeling policy demonstrates how Microsoft Purview can automatically classify healthcare-related information using built-in Sensitive Information Types.

The policy evaluates supported Microsoft 365 content and applies the **Confidential – PHI Data** sensitivity label when configured detection criteria are met.

## Policy Configuration

| Setting | Configuration |
| --- | --- |
| Policy Name | Auto-Label PHI |
| Label Applied | Confidential – PHI Data |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| Policy Mode | On |

## Detection Criteria

The policy uses Microsoft Purview built-in Sensitive Information Types including:

- Brand Medication Names
- Generic Medication Names
- Types of Medication
- Medicare Beneficiary Identifier (MBI)
- U.S. Individual Taxpayer Identification Number (ITIN)
- U.S. Social Security Number (SSN)

When the configured conditions are met, Microsoft Purview automatically applies the **Confidential – PHI Data** sensitivity label.

## Protection Flow

**Healthcare Data → Sensitive Information Type Detection → Auto-Labeling Policy → Confidential – PHI Data → DLP**

The applied sensitivity label can then be used as a condition by downstream DLP policies to apply additional data-protection controls.

## Key Takeaway

Auto-labeling provides consistent classification without relying entirely on users to recognize and manually label sensitive information.

Separating classification from enforcement also allows sensitivity labels to be reused across multiple data-protection policies.

## Disclaimer

All healthcare information, users, and organizations used for testing were fictional and created solely for this lab. This project demonstrates technical Microsoft Purview capabilities and does not represent or claim HIPAA compliance.
<img width="588" height="836" alt="image" src="https://github.com/user-attachments/assets/64e4d0a0-9592-462b-870c-90d58c3e378a" />
