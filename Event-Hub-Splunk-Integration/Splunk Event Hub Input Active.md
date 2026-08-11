# Microsoft Defender XDR Streaming API Configuration

Microsoft Defender XDR was configured to stream security telemetry to Azure Event Hubs for downstream ingestion into Splunk.

The streaming configuration provides the connection between Defender XDR security events and the Azure Event Hubs pipeline used by Splunk.

**Microsoft Defender XDR → Azure Event Hubs → Splunk**

## Configuration
<img width="1909" height="466" alt="image" src="https://github.com/user-attachments/assets/cb162e22-95cf-417d-84d7-e4d08b808b64" />

## Validation

The configuration was validated by confirming that Defender XDR alert telemetry was successfully received through Azure Event Hubs and later searchable in Splunk.

