# Block PCI External Sharing

## Overview

This DLP policy demonstrates how Microsoft Purview can protect payment card information from unauthorized external sharing.

The scenario uses fictional payment card data in a controlled Microsoft 365 lab environment.

## Policy Configuration

| Setting | Configuration |
| --- | --- |
| Policy Name | Block PCI External Sharing |
| Data Type | Payment Card Information |
| Location | Exchange Online |
| Sharing Condition | Recipient outside the organization |
| User Notifications | Enabled |
| Initial Deployment | Simulation |

## Policy Logic

The policy evaluates outbound content for payment card information and external-sharing activity.
<img width="1330" height="727" alt="image" src="https://github.com/user-attachments/assets/186104ec-5ba1-4825-9687-6c5c3745b4c1" />
When the conditions are met, the policy can:

- Detect payment card information
- Identify external-sharing attempts
- Notify the user
- Generate DLP activity for review
- Restrict external sharing when enforcement is enabled

## Testing

The policy was tested using fictional payment card data sent to an external test account.

Simulation was used to validate detection and policy behavior before enforcement.

**PCI Detection → External Sharing Condition → DLP Match → User Notification → Security Monitoring**

## Key Takeaway

This test demonstrated how Microsoft Purview DLP can combine sensitive-data detection with sharing context to protect payment card information while allowing policies to be validated before enforcement.

## Disclaimer

All payment card information, users, recipients, and organizations used in this scenario are fictional and were created solely for lab testing.


---

## Business Value

Payment card information is subject to strict security requirements under PCI DSS. This policy reduces the risk of accidental disclosure by preventing sensitive financial data from leaving the organization while providing administrators with visibility into attempted policy violations.

By integrating Microsoft Purview sensitivity labels with Data Loss Prevention policies, Knapp Healthcare enforces consistent protection of regulated financial information across Microsoft 365 services.


