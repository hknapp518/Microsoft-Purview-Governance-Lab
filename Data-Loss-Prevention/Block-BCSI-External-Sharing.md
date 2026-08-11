# Block BCSI External Sharing

## Overview

This policy demonstrates how Microsoft Purview DLP can use a custom Sensitive Information Type to detect and prevent external sharing of fictional BES Cyber System Information (BCSI).

The scenario was created as a NERC CIP-inspired data protection use case using synthetic lab data.

## Detection Logic

- **Sensitive Information Type:** BES Cyber System Information Identifier
- **Detection:** Custom regex with supporting contextual evidence
- **Location:** Exchange Online
- **Condition:** BCSI detected in content sent outside the organization
- **Action:** Block external sharing and generate an alert

## Testing

The policy was first deployed in **Simulation mode** to validate the custom SIT and external-sharing condition without blocking the message.

The simulation successfully detected:

- The custom BCSI identifier
- Supporting BCSI context
- An external recipient
- The matching DLP rule

After validation, the policy was moved into enforcement.

## Enforcement Result

A second test attempted to send the same fictional BCSI content to an external email account.

Microsoft Purview detected the custom SIT and blocked the message from being delivered.

**Result: PASS — External sharing blocked**

## Security Monitoring

The enforcement event generated a DLP alert in Microsoft Defender XDR.

The resulting security telemetry was streamed through Azure Event Hubs and ingested into Splunk, where the event was successfully identified as a Microsoft Data Loss Prevention alert associated with the BCSI enforcement test.

## Validation

**Custom BCSI SIT → DLP Match → External Sharing Blocked → Defender XDR → Azure Event Hubs → Splunk**

This test demonstrated how organization-specific data classification can be connected to preventative controls and downstream SOC monitoring.

## Disclaimer

The BCSI identifier and all associated data used in this scenario are fictional and were created solely for lab testing.

This is a NERC CIP-inspired information protection scenario and does not represent or claim compliance with a specific NERC CIP requirement.
<img width="1220" height="522" alt="image" src="https://github.com/user-attachments/assets/41e1f60f-2c6c-403b-bd53-ec5f4c088f9b" />
Simulation mode

<img width="1686" height="933" alt="image" src="https://github.com/user-attachments/assets/f14486fc-68c5-435f-8b8f-c46dc5e7eb0f" />

Policy turned on
