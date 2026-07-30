# Protect Clinical Research Protocols

## Overview

The **Protect Clinical Research Protocols** Data Loss Prevention (DLP) policy was created to prevent proprietary clinical research protocol identifiers from being shared outside of Knapp Healthcare.

Unlike traditional DLP policies that rely solely on Microsoft's built-in Sensitive Information Types, this policy uses a **Custom Sensitive Information Type** to detect organization-specific protocol identifiers and apply protection automatically.

---

## Purpose

The purpose of this policy is to protect Knapp Healthcare's proprietary clinical research protocol identifiers from unauthorized external sharing. By leveraging a Custom Sensitive Information Type, Microsoft Purview can automatically detect organization-specific protocol IDs and apply Data Loss Prevention (DLP) controls to reduce the risk of accidental disclosure.

---

## Business Scenario

Knapp Healthcare conducts clinical research using an internal protocol numbering convention that uniquely identifies research initiatives.

Example:

```text
KNAPP-PROT-2026-001
```

These identifiers represent confidential research projects and should not be shared outside the organization.

Since Microsoft's built-in Sensitive Information Types cannot identify these proprietary identifiers, a **Custom Sensitive Information Type** was created using a regular expression and integrated into this DLP policy.

---

## Policy Configuration

| Setting | Configuration |
|----------|---------------|
| Policy Name | Protect Clinical Research Protocols |
| Rule | Block Clinical Protocol External Sharing |
| Detection Method | Custom Sensitive Information Type |
| Sensitive Information Type | Knapp Clinical Protocol Identifier |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| Deployment Mode | Simulation |
| Email Notifications | Enabled |

---

## Rule Logic

The DLP policy monitors supported Microsoft 365 locations for content containing the **Knapp Clinical Protocol Identifier** Custom Sensitive Information Type.

When a protocol identifier is detected, the policy:

- Detects the custom protocol identifier
- Displays a policy tip
- Sends a user notification
- Blocks unauthorized external sharing
- Generates policy matches for administrator review
- Operates in **Simulation Mode** prior to enforcement

---

## Custom Detection

The policy relies on a Custom Sensitive Information Type developed specifically for Knapp Healthcare.

Example Identifier:

```text
KNAPP-PROT-2026-001
```

The Custom Sensitive Information Type uses a regular expression to identify protocol identifiers that are unique to the organization and cannot be detected using Microsoft's built-in Sensitive Information Types.

---

## Business Value

This implementation demonstrates how Microsoft Purview can protect organization-specific intellectual property through custom data classification.

By combining a Custom Sensitive Information Type with Microsoft Purview Data Loss Prevention, Knapp Healthcare can automatically identify proprietary research documentation, reduce the risk of accidental external disclosure, and validate policy behavior using Simulation Mode before enforcing production controls.

---

## Screenshots

- DLP Policy Overview
- DLP Rule Configuration
- Custom Sensitive Information Type Detection
- Policy Summary (Simulation Mode)<img width="1306" height="738" alt="image" src="https://github.com/user-attachments/assets/210f7e90-5778-492b-a910-25547075f9c1" />
<img width="631" height="878" alt="image" src="https://github.com/user-attachments/assets/23aa15fb-b291-42af-baed-d85b74878f7b" />
