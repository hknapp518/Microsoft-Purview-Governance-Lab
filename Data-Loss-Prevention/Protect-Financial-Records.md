# Protect Financial Records

## Overview

This DLP policy demonstrates how Microsoft Purview can detect and protect sensitive financial information across Microsoft 365.

The scenario uses fictional financial data in a controlled lab environment.

## Policy Configuration

| Setting | Configuration |
| --- | --- |
| Policy Name | Protect Financial Records |
| Detection Method | Sensitive Information Types |
| Data Type | Financial information |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| User Notifications | Enabled |

## Policy Logic

The policy evaluates content for sensitive financial information and applies the configured DLP controls when a match occurs.

When the policy conditions are met, Purview can:

- Detect sensitive financial information
- Generate DLP activity for review
- Notify users when applicable
- Apply configured protection controls

## Validation

The policy was tested using fictional financial information to validate that Microsoft Purview could identify the sensitive data and trigger the associated DLP rule.

**Financial Data → Sensitive Information Detection → DLP Match → Protection**

## Key Takeaway

Built-in Sensitive Information Types provide a way to identify common financial data without requiring a custom classifier for every data type.

## Disclaimer

All financial information, users, and organizations used in this scenario are fictional and were created solely for lab testing.

---
<img width="531" height="697" alt="image" src="https://github.com/user-attachments/assets/0534c26f-bb23-4b53-a71d-ae7d1c9d9ca9" />
<img width="1287" height="730" alt="image" src="https://github.com/user-attachments/assets/40600d11-088a-4718-abd6-b5956c3f4145" />
