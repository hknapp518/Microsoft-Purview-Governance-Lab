# Purview DLP Alert Ingested into Splunk

## Overview

This test validates that Microsoft Purview DLP alert telemetry generated in Microsoft Defender XDR was successfully streamed through Azure Event Hubs and ingested into Splunk.

The source event was generated from a controlled PHI external-sharing test.

## Splunk Validation

The `purview` index was searched for Defender `AlertInfo` telemetry received through the Azure Event Hubs input.

```spl
index=purview sourcetype="mscs:azure:eventhub" category="AdvancedHunting-AlertInfo"
| table _time properties.Title properties.Category properties.Severity properties.ServiceSource properties.DetectionSource properties.AlertId
```

<img width="1844" height="853" alt="image" src="https://github.com/user-attachments/assets/df02ce80-987b-4a23-badd-36bb4cdf1653" />
Figure: Microsoft Purview DLP Alert Ingested into Splunk via Azure Event Hub
Splunk successfully ingested the Microsoft Defender XDR AlertInfo event generated when the Block PHI External Sharing DLP policy prevented a PHI-labeled email from being sent to an external recipient. This validates the security monitoring pipeline from Microsoft Purview → Defender XDR → Azure Event Hub → Splunk.

The event was successfully identified in Splunk with:

- **Category:** Exfiltration
- **Severity:** Low
- **Service Source:** Microsoft Data Loss Prevention
- **Detection Source:** Microsoft Data Loss Prevention
- **Alert ID:** Matching the source Defender XDR alert

## Result

**PASS — Microsoft Purview DLP alert telemetry successfully ingested into Splunk.**

The test validated the monitoring path:

**Microsoft Purview DLP → Defender XDR → Azure Event Hubs → Splunk**
