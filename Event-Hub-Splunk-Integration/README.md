# Defender XDR → Azure Event Hubs → Splunk Integration

## Overview

This integration demonstrates how Microsoft Defender XDR security telemetry can be streamed through Azure Event Hubs and ingested into Splunk for investigation.

The goal was to move beyond manual event exports and validate an automated monitoring path for Microsoft Purview DLP alerts.

## Architecture

**Microsoft Purview DLP → Microsoft Defender XDR → Defender Streaming API → Azure Event Hubs → Splunk Enterprise**

## Configuration

Microsoft Defender XDR was configured to stream Advanced Hunting telemetry to a dedicated Azure Event Hub.

The following event types were enabled:

- `AlertInfo`
- `AlertEvidence`

A dedicated Microsoft Entra service principal was used to provide Splunk access to the Event Hub with the **Azure Event Hubs Data Receiver** role.

Splunk was configured using the Microsoft Cloud Services add-on with:

- **Index:** `purview`
- **Sourcetype:** `mscs:azure:eventhub`

## Validation

A controlled PHI external-sharing test was used to generate a Microsoft Purview DLP alert.

The resulting event was validated in Microsoft Defender XDR using Advanced Hunting and then located in Splunk after being streamed through Azure Event Hubs.

The Splunk event retained key alert fields including:

- Alert title
- Category
- Severity
- Service source
- Detection source
- Alert ID

The Alert ID provided a correlation point between the source event in Defender XDR and the event received in Splunk.

## Splunk Query

```spl
index=purview sourcetype="mscs:azure:eventhub" category="AdvancedHunting-AlertInfo"
| table _time properties.Title properties.Category properties.Severity properties.ServiceSource properties.DetectionSource properties.AlertId
```

## Result

**PASS — Microsoft Purview DLP alert telemetry was successfully streamed from Defender XDR through Azure Event Hubs and ingested into Splunk.**

**Purview DLP → Defender XDR → Azure Event Hubs → Splunk**

## Evidence

- Defender XDR Streaming API configuration
- Splunk Azure Event Hub input configuration
- Defender XDR `AlertInfo` validation
- Purview DLP alert ingested into Splunk

## Key Takeaway

DLP enforcement is only part of the data-protection process. Security telemetry also needs to reach the monitoring platform used by analysts for investigation and correlation.

This integration demonstrated how Purview DLP events can move from data protection controls into a centralized SIEM workflow.

## Disclaimer

All organizations, users, identifiers, and sensitive information used in this integration are fictional and were created solely for lab testing.
