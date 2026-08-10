# BES Cyber System Information (BCSI) Custom Sensitive Information Type

## Overview

A custom Microsoft Purview Sensitive Information Type (SIT) was created to identify organization-specific information associated with BES Cyber System Information (BCSI).

The classifier demonstrates how Microsoft Purview can use custom regular expressions and contextual evidence to identify sensitive information that is not covered by a built-in Sensitive Information Type.

> **Lab Note:** The BCSI identifier format used in this project is fictional and was created solely for security testing. It is not an identifier format prescribed by NERC.

---

## Detection Pattern

The custom SIT detects identifiers using the following lab format:

`BES-BCSI-YYYY-NNNN`

Example:

`BES-BCSI-2026-0001`

### Primary Element

**Regex ID:** `BES_BCSI_Identifier_Regex`

**Regular Expression:**

`(?:^|\s)(BES-BCSI-\d{4}-\d{4})(?:$|\s)`

The regular expression identifies the structured BCSI identifier used throughout the lab.

<img width="635" height="777" alt="image" src="https://github.com/user-attachments/assets/8296e057-6542-46b1-bc33-62666b0feb1c" />


---

## Supporting Evidence

A supporting keyword list named `BCSI_Supporting_Keywords` was added to provide contextual validation.

Keywords include:

- BES Cyber System Information
- BES Cyber System
- BCSI
- Bulk Electric System
- Electronic Security Perimeter
- Control Center
- Substation
- NERC CIP

---

## Detection Configuration

The custom SIT was configured with:

- **Confidence level:** High
- **Primary element:** `BES_BCSI_Identifier_Regex`
- **Supporting element:** `BCSI_Supporting_Keywords`
- **Character proximity:** 300 characters
- **Match type:** Word match

The identifier and supporting terminology must occur within 300 characters of each other. This adds contextual evidence to the structured identifier and helps reduce false positive detections.

---

## Validation

A controlled test document containing the following fictional data was uploaded to the Microsoft Purview Sensitive Information Type testing interface:

`BES-BCSI-2026-0001`

The document also contained supporting terminology including **BCSI**, **BES Cyber System**, and **Control Center**.

Microsoft Purview successfully identified the custom BCSI identifier and produced a **High-confidence match**, validating the regex and supporting keyword detection logic.

<img width="637" height="731" alt="image" src="https://github.com/user-attachments/assets/9b880b38-6348-4c24-921a-1bfc1bc7020e" />



## DLP Integration

The custom SIT is used by the **Block BCSI External Sharing** DLP policy.

The policy is designed to identify BCSI content being transmitted to recipients outside the organization and apply protective controls including:

- External sharing restriction
- User notification and policy tips
- Administrative alert generation

This creates an end-to-end security workflow:

**Custom SIT → BCSI Detection → DLP Policy → External Sharing Control → Defender Alert → Azure Event Hub → Splunk**

---

