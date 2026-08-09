# Microsoft Defender XDR → Azure Event Hub → Splunk Integration

## Overview

This section demonstrates an automated security monitoring pipeline that forwards Microsoft Purview Data Loss Prevention (DLP) alerts from Microsoft Defender XDR into Splunk using Azure Event Hubs.

The goal was to move beyond manually exporting Purview activity and importing CSV files into Splunk by implementing automated security telemetry ingestion.

## Architecture

Microsoft Purview DLP  
↓  
Microsoft Defender XDR  
↓  
Defender XDR Streaming API  
↓  
Azure Event Hub  
↓  
Splunk Enterprise

## Integration Configuration

### Microsoft Defender XDR

Microsoft Defender XDR was configured to stream security telemetry using the Streaming API.

The following Advanced Hunting event types were enabled:

- `AlertInfo`
- `AlertEvidence`

These events were configured to stream to an Azure Event Hub for downstream SIEM ingestion.

### Azure Event Hub

An Azure Event Hubs namespace and dedicated Event Hub were created to provide the streaming pipeline between Microsoft Defender XDR and Splunk.

A dedicated Microsoft Entra application was created for Splunk:

`Splunk-EventHub-Consumer`

The application was assigned the **Azure Event Hubs Data Receiver** RBAC role, providing least-privilege access to consume events from the Event Hub.

### Splunk

The **Splunk Add-on for Microsoft Cloud Services** was installed and configured to consume events from Azure Event Hubs.

Incoming Event Hub telemetry was stored in the Splunk index:

`purview`

with the sourcetype:

`mscs:azure:eventhub`

## End-to-End Validation

A controlled DLP test was performed using fictitious clinical data.

A Microsoft Word document containing simulated PHI was classified with the **Confidential – PHI Data** sensitivity label and attached to an email addressed to an external recipient.

Microsoft Purview detected the attempted external sharing and enforced the **Block PHI External Sharing** DLP policy.

The configured rule performed the following actions:

- `BlockAccess`
- `NotifyUser`
- `GenerateAlert`

The message was prevented from being delivered externally and a low-severity DLP alert was generated.

## Defender XDR Alert Validation

Microsoft Defender XDR Advanced Hunting was used to verify that the DLP violation generated an `AlertInfo` event.

The event was categorized as **Exfiltration** and identified Microsoft Data Loss Prevention as both the service and detection source.

<img width="1201" height="702" alt="image" src="https://github.com/user-attachments/assets/64482cbb-9192-470a-ae11-a316c7877f44" />


**Figure: Microsoft Purview DLP Alert Validated in Defender XDR Advanced Hunting**

Advanced Hunting confirms that the blocked PHI external-sharing attempt generated a Microsoft Data Loss Prevention `AlertInfo` event categorized as Exfiltration. This validates the Defender XDR stage of the monitoring pipeline.

## Splunk Event Hub Validation

Splunk was queried for Microsoft Defender telemetry received through Azure Event Hub.

The following SPL query was used to isolate `AlertInfo` events:

<img width="1844" height="853" alt="image" src="https://github.com/user-attachments/assets/60d1914a-97a0-41ea-90d9-507e74cc5346" />


# Defender XDR → Azure Event Hub → Splunk Integration

## Overview

This integration demonstrates an automated security monitoring pipeline that forwards Microsoft Purview DLP alerts from Microsoft Defender XDR into Splunk through Azure Event Hubs.

The objective was to replace manual CSV exports with automated security telemetry ingestion and demonstrate how DLP events can be centralized in an enterprise SIEM for investigation.

## Architecture

**Microsoft Purview DLP → Microsoft Defender XDR → Defender Streaming API → Azure Event Hub → Splunk Enterprise**

---

## 1. Defender XDR Streaming Configuration

Microsoft Defender XDR was configured to stream Advanced Hunting telemetry to a dedicated Azure Event Hub.

The following event types were enabled:

- `AlertInfo`
- `AlertEvidence`

<img width="762" height="784" alt="image" src="https://github.com/user-attachments/assets/f5af1334-25a4-431a-a860-219c90fd57dc" />


**Figure 1 – Defender XDR Streaming API Configuration**

Defender XDR was configured to forward `AlertInfo` and `AlertEvidence` telemetry to the Azure Event Hub used for downstream Splunk ingestion.

---

## 2. Secure Event Hub Access

A dedicated Microsoft Entra application, `Splunk-EventHub-Consumer`, was created for Splunk.

The service principal was assigned the **Azure Event Hubs Data Receiver** role, providing least-privilege access required to consume security telemetry from the Event Hub.

![Azure Event Hub RBAC](event-hub-rbac-data-receiver.png)

**Figure 2 – Azure Event Hub RBAC Configuration**

The Splunk service principal was granted the Azure Event Hubs Data Receiver role rather than broader Azure permissions.

---

## 3. Splunk Event Hub Input

The Splunk Add-on for Microsoft Cloud Services was configured to consume events from Azure Event Hubs.

Events were ingested into:

- **Index:** `purview`
- **Sourcetype:** `mscs:azure:eventhub`

![Splunk Event Hub Input](splunk-event-hub-input-active.png)

**Figure 3 – Active Splunk Azure Event Hub Input**

The Azure Event Hub input is active in Splunk and configured for automated security telemetry ingestion.

---

## 4. End-to-End DLP Test

A controlled test was performed using fictitious clinical data.

A Word document containing simulated PHI was classified with the **Confidential – PHI Data** sensitivity label and attached to an email addressed to an external recipient.

The **Block PHI External Sharing** DLP policy detected the attempted external transmission and performed the following actions:

- `BlockAccess`
- `NotifyUser`
- `GenerateAlert`

The message was prevented from being delivered externally.

---

## 5. Defender XDR Validation

Microsoft Defender XDR Advanced Hunting confirmed that the DLP violation generated an `AlertInfo` event.

The event was categorized as **Exfiltration** with Microsoft Data Loss Prevention identified as the detection source.

![Defender XDR AlertInfo Event](defender-alertinfo-dlp-event.png)

**Figure 4 – DLP Alert Validated in Defender XDR**

Advanced Hunting confirms that the blocked PHI external-sharing attempt generated the Defender telemetry required for downstream streaming.

---

## 6. Splunk Validation

The following SPL query was used to isolate Defender `AlertInfo` events received through Azure Event Hub:

<img width="762" height="784" alt="image" src="https://github.com/user-attachments/assets/f5af1334-25a4-431a-a860-219c90fd57dc" />
