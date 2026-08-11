# Defender XDR DLP Alert Validation

## Overview

Before validating the Event Hubs and Splunk integration, I confirmed that the Microsoft Purview DLP alert was available in Microsoft Defender XDR.

The alert was generated from a controlled PHI external-sharing test.

## Defender XDR Validation

The `AlertInfo` table was queried using Advanced Hunting:

```kql
AlertInfo
| where Timestamp > ago(1h)
| order by Timestamp desc
```
<img width="1201" height="702" alt="image" src="https://github.com/user-attachments/assets/cbe9ff83-c1d0-496a-a1d9-eed756e472e6" />

Microsoft Defender XDR was configured to stream AlertInfo and AlertEvidence telemetry to the dedicated Azure Event Hub for downstream SIEM ingestion.
