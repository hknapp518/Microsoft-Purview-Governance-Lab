# DLP Investigation — Clinical Protocol External Sharing

## Overview

This investigation documents the validation of a Microsoft Purview DLP policy designed to detect a custom Clinical Protocol Identifier when shared outside the organization.

The test was performed using synthetic lab data in a controlled Microsoft 365 environment.

---

## Detection Scenario

The DLP policy monitored Exchange Online for messages containing the custom **Clinical Protocol Identifier** Sensitive Information Type (SIT) being sent to an external recipient.

### Detection Logic

- **Location:** Exchange Online
- **Sensitive Information Type:** Clinical Protocol Identifier
- **Sharing Condition:** Recipient outside the organization
- **Policy Mode:** Simulation with notifications
- **Test Data:** Synthetic clinical research information

The custom SIT was designed using a regular expression and supporting contextual evidence to identify fictional clinical protocol identifiers.

---

## Test Activity

A test email containing the custom Clinical Protocol Identifier was sent from an internal Microsoft 365 account to an external test account.

The purpose of the test was to validate that Purview could:

1. Detect the custom Sensitive Information Type.
2. Recognize the external-sharing condition.
3. Match the appropriate DLP rule.
4. Generate security telemetry for investigation.

---

## Activity Explorer Validation

The test activity was reviewed in Microsoft Purview Activity Explorer.

The event confirmed that the custom Sensitive Information Type and DLP policy matched the Exchange Online activity as expected.

<!-- Insert Activity Explorer screenshot here -->

**Result:** Custom SIT and external-sharing condition successfully detected.

---

## DLP Alert

Microsoft Purview generated a DLP alert associated with the test activity.

The alert provided visibility into the matched policy, affected workload, activity, and information required for analyst review.

<!-- Insert DLP alert screenshot here -->

---

## Alert Triage

The alert was reviewed and determined to be an authorized validation test using synthetic information.

**Classification:** Benign positive  
**Remediation required:** None

<img width="673" height="741" alt="image" src="https://github.com/user-attachments/assets/dd19d6d6-6688-49af-ac00-097dc0893368" />

The detection itself was accurate, but the activity was intentionally generated to validate the DLP control. No production or sensitive data was exposed.

---

## Validation Result

**PASS**

**Custom SIT → External Sharing Condition → DLP Rule Match → Activity Explorer → DLP Alert → Analyst Investigation → Benign Positive**

The test confirmed that the custom classification and DLP detection logic operated as expected against Exchange Online activity.

---

## Key Takeaway

Simulation mode allowed the custom SIT and DLP detection logic to be validated against actual Exchange Online activity before enforcement.

This provided an opportunity to confirm detection accuracy, investigate the resulting alert, and identify potential false positives before moving the policy into enforcement.

---

## Disclaimer

This investigation was performed in a controlled lab environment using fictional organizations, identifiers, users, and test data. No real patient, clinical research, or other sensitive information was used.



