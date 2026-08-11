# Protect Clinical Research Protocols

## Overview

This DLP policy demonstrates how Microsoft Purview can use a Custom Sensitive Information Type (SIT) to detect organization-specific clinical research identifiers.

The scenario uses a fictional clinical research organization and synthetic test data.

## Business Scenario

The organization uses an internal naming convention to identify clinical research protocols.

Example:

`KNAPP-PROT-2026-001`

Because the identifier is organization-specific, a Custom Sensitive Information Type was created using a regular expression rather than relying on Microsoft's built-in SITs.

## Policy Configuration

| Setting | Configuration |
| --- | --- |
| Policy Name | Protect Clinical Research Protocols |
| Rule | Block Clinical Protocol External Sharing |
| Detection Method | Custom Sensitive Information Type |
| Sensitive Information Type | Knapp Clinical Protocol Identifier |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| Deployment Mode | Simulation |
| User Notifications | Enabled |

## Detection and Policy Logic
<img width="1306" height="738" alt="image" src="https://github.com/user-attachments/assets/210f7e90-5778-492b-a910-25547075f9c1" />
The policy monitors supported Microsoft 365 locations for the custom Clinical Protocol Identifier.

When matching content is detected, the policy can:

- Identify the custom protocol identifier
- Evaluate external-sharing activity
- Display policy tips and user notifications
- Generate policy matches for administrator review
- Apply external-sharing restrictions when moved into enforcement

Simulation mode was used first to validate detection and policy behavior before enabling enforcement.

## Validation

Testing confirmed that the custom SIT could identify the fictional protocol format and trigger the associated DLP policy during controlled external-sharing tests.

The resulting activity was also reviewed through Microsoft Purview as part of the DLP investigation workflow.

**Custom SIT → DLP Match → External Sharing Detection → Alert → Investigation**

## Key Takeaway

Custom Sensitive Information Types allow Purview DLP policies to protect organization-specific information that may not be covered by Microsoft's built-in classifiers.

This scenario also demonstrated the value of validating custom detection logic in simulation before moving a policy into enforcement.

## Disclaimer

All organizations, identifiers, users, and clinical research information used in this scenario are fictional and were created solely for lab testing.

---

