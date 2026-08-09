
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

<img width="1456" height="532" alt="image" src="https://github.com/user-attachments/assets/7aa933ee-680d-4589-aab4-66e227e30532" />


**Figure 2 – Azure Event Hub RBAC Configuration**

The Splunk service principal was granted the Azure Event Hubs Data Receiver role rather than broader Azure permissions.

---

## 3. Splunk Event Hub Input

The Splunk Add-on for Microsoft Cloud Services was configured to consume events from Azure Event Hubs.

Events were ingested into:

- **Index:** `purview`
- **Sourcetype:** `mscs:azure:eventhub`

<img width="1909" height="466" alt="image" src="https://github.com/user-attachments/assets/1280d1f8-cb25-4c16-b170-e682835d74e4" />


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

<img width="1201" height="702" alt="image" src="https://github.com/user-attachments/assets/a833c115-54b9-44bd-b76d-52b33ae61126" />


**Figure 4 – DLP Alert Validated in Defender XDR**

Advanced Hunting confirms that the blocked PHI external-sharing attempt generated the Defender telemetry required for downstream streaming.

---

## 6. Splunk Validation

The following SPL query was used to isolate Defender `AlertInfo` events received through Azure Event Hub:

spl: index=purview sourcetype="mscs:azure:eventhub" category="AdvancedHunting-AlertInfo"

| table _time properties.Title properties.Category properties.Severity properties.ServiceSource properties.DetectionSource properties.AlertId

<img width="1844" height="853" alt="image" src="https://github.com/user-attachments/assets/1af1bcd7-df5d-423d-bc4d-90e52fa7f34f" />

