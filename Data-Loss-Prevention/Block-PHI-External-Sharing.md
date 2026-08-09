# Block PHI External Sharing

## Overview

To reduce the risk of unauthorized disclosure of Protected Health Information (PHI), a Microsoft Purview Data Loss Prevention (DLP) policy was implemented to prevent externally sharing content classified as **Confidential – PHI Data**.

The policy monitors Exchange Online, SharePoint Online, and OneDrive to ensure that sensitive healthcare information remains within the organization.

---

## Policy Configuration

**Policy Name**

Block PHI External Sharing

**Protected Label**

Confidential – PHI Data

**Protected Locations**

- Exchange Online
- SharePoint Online
- OneDrive

**Policy Mode**

Enabled

---

## Implementation

The DLP policy detects documents that have been classified with the **Confidential – PHI Data** sensitivity label and prevents those files from being shared externally. By enforcing protection at the Microsoft 365 service level, the organization reduces the likelihood of accidental disclosure of regulated healthcare information.

<img width="598" height="809" alt="image" src="https://github.com/user-attachments/assets/30b6f809-441f-43a6-9a73-88e147b56a47" />
<img width="1227" height="713" alt="image" src="https://github.com/user-attachments/assets/1fc7e6b9-60af-4df3-b782-1196f44a3667" />


---

## Validation Testing

A controlled PHI test document was labeled **Confidential – PHI Data** and attached to an Exchange Online email addressed to an external recipient.

The DLP policy successfully detected the external sharing attempt and enforced the configured rule.

### Enforcement Result

- Activity: `DlpRuleMatch`
- Location: Exchange
- Policy: `Block PHI External Sharing`
- Rule: `Block PHI Labeled Content External Sharing`
- Sensitivity Label: `Confidential – PHI Data`
- Actions: `BlockAccess`, `NotifyUser`, `GenerateAlert`
- Result: External delivery blocked

The sender received a policy notification confirming that the message was not delivered to the external recipient.

### Defender Investigation

The DLP match generated a Microsoft Defender alert categorized as **Exfiltration** and was automatically correlated into a Defender incident.

The incident provided an investigation view connecting the user, DLP alert, activity, and protected email event.
<img width="1875" height="896" alt="image" src="https://github.com/user-attachments/assets/d5681b34-9126-4ed7-b5a2-370c7efefe52" />
