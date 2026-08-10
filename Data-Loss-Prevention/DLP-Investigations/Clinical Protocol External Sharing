# DLP Investigation – Clinical Protocol External Sharing

## Investigation Summary

A controlled Microsoft Purview DLP test was performed to validate detection of a custom Sensitive Information Type (SIT) representing internal clinical research protocol identifiers.

A synthetic clinical protocol identifier was included in an Exchange Online email and sent to an external Gmail recipient.

Microsoft Purview successfully detected the custom identifier, matched the configured DLP policy, generated an alert, and recorded the activity for investigation.

All information used during testing was synthetic.

---

## Test Scenario

**User:** Clinical Systems Analyst  
**Workload:** Exchange Online  
**Destination:** External email recipient  
**Test Identifier:** `KNAPP-PROT-2026-001`  
**Sensitive Information Type:** Knapp Clinical Protocol Identifier

The test email contained a synthetic clinical research protocol identifier matching the custom SIT pattern and was sent to a recipient outside the Microsoft 365 organization.

---

## DLP Policy

**Policy:** Protect Clinical Research Protocols  
**Rule:** Block Clinical Protocol External Sharing  
**Policy Mode:** Simulation with notifications

### Detection Conditions

The rule evaluated content for:

- Knapp Clinical Protocol Identifier
- Content shared with users outside the organization
- Exchange email message body

### Configured Actions

When the rule matched, Microsoft Purview was configured to:

- Notify the user
- Generate an administrator alert
- Generate an incident report

---

## Investigation

Microsoft Purview Activity Explorer recorded a **DLP rule matched** event.

Investigation of the event confirmed:

- The activity originated from Exchange Online.
- The recipient was external to the organization.
- The custom `Knapp Clinical Protocol Identifier` SIT was detected.
- Sensitive information was detected in the email message body.
- The `Protect Clinical Research Protocols` policy matched.
- The `Block Clinical Protocol External Sharing` rule matched.
- No user override was performed.
- An administrator alert and incident report were generated.

The DLP alert was subsequently reviewed through the Microsoft Purview Alerts interface.

---

## Alert Triage

<img width="673" height="741" alt="image" src="https://github.com/user-attachments/assets/dd19d6d6-6688-49af-ac00-097dc0893368" />

The alert was assigned to the Clinical Systems Analyst for investigation.

The activity was determined to be an authorized DLP validation test using synthetic information.

**Classification:** Benign positive

This classification was selected because the DLP detection was accurate, but the activity was intentionally generated as part of an authorized security-control validation.

---

## Analyst Disposition

No actual sensitive or production data was exposed.

The custom Sensitive Information Type successfully identified the synthetic clinical protocol identifier and generated the expected DLP telemetry.

The policy was operating in **simulation with notifications**, allowing detection behavior to be validated before enabling production enforcement.

**Final disposition:** Benign positive  
**Remediation required:** None

---

## Validation Result

**PASS**

The test successfully validated the following control chain:

Custom Clinical Protocol Identifier  
→ Sensitive Information Type Detection  
→ External Sharing Condition  
→ DLP Rule Match  
→ Activity Explorer Event  
→ Administrator Alert  
→ Analyst Investigation  
→ Benign Positive Classification  
→ Alert Resolution

---

## Security Engineering Takeaway

Microsoft Purview DLP simulation mode provides a method for validating detection logic and evaluating policy behavior before enforcing restrictive controls.

Testing the custom Sensitive Information Type against Exchange Online activity demonstrated that the detection logic functioned against real Microsoft 365 workload activity rather than only within policy configuration.

This approach allows security teams to validate policy accuracy and investigate potential false positives before transitioning a DLP policy into enforcement mode.
