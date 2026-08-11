# BES Cyber System Information (BCSI) Identifier

## Overview

This Custom Sensitive Information Type (SIT) was created to detect fictional BES Cyber System Information (BCSI) identifiers in Microsoft 365 content.

The classifier supports a NERC CIP-inspired lab scenario focused on identifying and protecting organization-specific sensitive information.

## Detection Logic

The custom SIT combines a regular expression with supporting contextual evidence.

### Primary Pattern

```regex
BES-BCSI-\d{4}-\d{4}
```

Example test identifier:

```text
BES-BCSI-2026-0001
```
<img width="635" height="777" alt="image" src="https://github.com/user-attachments/assets/8296e057-6542-46b1-bc33-62666b0feb1c" />
### Supporting Evidence

Contextual keywords were added to increase detection confidence and reduce matches based solely on the identifier pattern.

Examples include terms associated with the fictional BCSI scenario, such as:

- BES Cyber System Information
- BCSI
- Control Center
- Network Configuration
- Security Configuration

## Detection Approach

**Regex Pattern + Contextual Evidence → Custom SIT Match**

Using both pattern matching and supporting context provides stronger classification than relying on the identifier format alone.

## DLP Integration

The custom SIT was connected to the **Block BCSI External Sharing** DLP policy.

Testing demonstrated:

**Custom BCSI SIT → DLP Detection → External Sharing Attempt → Message Blocked → Defender XDR Alert → Azure Event Hubs → Splunk**

This allowed the custom classification to drive both preventative controls and downstream security monitoring.
<img width="637" height="731" alt="image" src="https://github.com/user-attachments/assets/9b880b38-6348-4c24-921a-1bfc1bc7020e" />
## Key Takeaway

Custom Sensitive Information Types allow Microsoft Purview to identify organization-specific information that may not be covered by built-in classifiers.

Adding contextual evidence to regex-based detection can also improve classification confidence and help reduce false positives.

## Disclaimer

The BCSI identifier, detection pattern, keywords, and associated test data used in this project are fictional and were created solely for lab testing.

This is a NERC CIP-inspired information-protection scenario and does not represent or claim compliance with a specific NERC CIP requirement.
