# Block PCI External Sharing

## Overview

To protect payment card information and support PCI DSS compliance, a Microsoft Purview Data Loss Prevention (DLP) policy was implemented to prevent externally sharing content classified as **Highly Confidential – PCI Data**.

The policy applies across Exchange Online, SharePoint Online, and OneDrive to reduce the risk of unauthorized disclosure of sensitive financial information.

---

## Policy Configuration

**Policy Name**

Block PCI External Sharing

**Protected Label**

Highly Confidential – PCI Data

**Protected Locations**

- Exchange Online
- SharePoint Online
- OneDrive

**Policy Mode**

Enabled

---

## Enforcement Actions

When content labeled **Highly Confidential – PCI Data** is detected, the policy:

- Blocks external sharing.
- Displays policy tips to educate users.
- Sends administrator alerts.
- Generates incident reports for security monitoring.

<img width="1330" height="727" alt="image" src="https://github.com/user-attachments/assets/186104ec-5ba1-4825-9687-6c5c3745b4c1" />


---

## Business Value

Payment card information is subject to strict security requirements under PCI DSS. This policy reduces the risk of accidental disclosure by preventing sensitive financial data from leaving the organization while providing administrators with visibility into attempted policy violations.

By integrating Microsoft Purview sensitivity labels with Data Loss Prevention policies, Knapp Healthcare enforces consistent protection of regulated financial information across Microsoft 365 services.


