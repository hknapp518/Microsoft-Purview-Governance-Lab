# Data Loss Prevention

## Overview

This section documents the Microsoft Purview DLP policies created and tested throughout the project.

The policies demonstrate multiple approaches to protecting sensitive information, including sensitivity labels, built-in Sensitive Information Types, and custom Sensitive Information Types.

## Policies

| Policy | Detection Method | Purpose |
| --- | --- | --- |
| Block PHI External Sharing | Sensitivity Label | Prevent externally sharing content classified as PHI |
| Block PCI External Sharing | Sensitivity Label | Prevent externally sharing content classified as PCI |
| Protect Financial Records | Built-in Sensitive Information Types | Detect and protect financial information |
| Block Custom Protocol SIT | Custom Sensitive Information Type | Detect fictional clinical research identifiers |
| Block BCSI External Sharing | Custom Sensitive Information Type | Detect and prevent external sharing of fictional BCSI content |

## Testing Approach

Policies were tested using fictional data and controlled external-sharing scenarios.

Testing included:

- Simulation mode
- Policy match validation
- User notifications
- False-positive review
- Enforcement testing
- External-sharing blocks
- Defender XDR alert validation
- Splunk telemetry validation

## Featured Test: BCSI External Sharing

The final DLP test used a custom Sensitive Information Type designed to identify a fictional BES Cyber System Information (BCSI) identifier.

The policy was first validated in simulation mode before being moved into enforcement.

The enforcement test successfully blocked the external email and generated a Microsoft Defender XDR alert. The resulting security telemetry was then streamed through Azure Event Hubs and validated in Splunk.

**Custom BCSI SIT → DLP Match → External Sharing Blocked → Defender XDR → Azure Event Hubs → Splunk**

> The BCSI scenario uses fictional lab data and is NERC CIP-inspired. It does not represent or claim compliance with a specific NERC CIP requirement.
