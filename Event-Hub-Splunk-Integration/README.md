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


