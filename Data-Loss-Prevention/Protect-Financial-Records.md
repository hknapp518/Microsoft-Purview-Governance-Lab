# Protect Financial Records

## Overview

The **Protect Financial Records** Data Loss Prevention (DLP) policy helps prevent the unauthorized external sharing of sensitive financial information across Microsoft 365 services. This policy detects built-in financial sensitive information types and automatically restricts external access to reduce the risk of payroll, banking, and financial data exposure.

---

## Business Scenario

Following a data governance assessment at **Knapp Healthcare**, it was determined that financial records, including payroll information and banking data, required additional protection from accidental or unauthorized external sharing.

To reduce organizational risk and support financial data protection requirements, a DLP policy was implemented to detect financial information and prevent it from being shared outside the organization.

---

## Policy Configuration

| Setting | Value |
|---------|-------|
| Policy Name | Protect Financial Records |
| Priority | 2 |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| Detection Method | Built-in Sensitive Information Types |
| Mode | Simulation with Notifications |

### Sensitive Information Types

- Credit Card Number
- International Banking Account Number (IBAN)
- SWIFT Code (Bank Identifier Code)
- U.S. Bank Account Number

All sensitive information types were configured using **High Confidence** detection with an instance count of **1 or more**.

---

## Enforcement Actions

When financial information is detected and shared externally, the policy:

- Restricts external access to protected content
- Blocks sharing with users outside the organization
- Displays policy tips to end users
- Sends incident reports to administrators
- Generates audit events for monitoring and investigation

---
<img width="531" height="697" alt="image" src="https://github.com/user-attachments/assets/0534c26f-bb23-4b53-a71d-ae7d1c9d9ca9" />
<img width="1287" height="730" alt="image" src="https://github.com/user-attachments/assets/40600d11-088a-4718-abd6-b5956c3f4145" />

## Business Value

This policy strengthens the organization's financial data protection strategy by reducing the likelihood of accidental disclosure of payroll, banking, and payment-related information. By leveraging Microsoft Purview's built-in Sensitive Information Types, the organization can automatically identify and protect regulated financial data while maintaining visibility into policy activity and compliance.
