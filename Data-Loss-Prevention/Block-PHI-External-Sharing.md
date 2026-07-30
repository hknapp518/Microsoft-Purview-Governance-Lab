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

![Block PHI External Sharing Policy](Screenshots/block-phi-external-sharing-policy.png)

---

## Business Value

Healthcare organizations are responsible for protecting patient information under HIPAA and other privacy regulations. This policy helps ensure that PHI remains within approved organizational boundaries by automatically preventing external sharing of protected content.

Implementing DLP alongside Microsoft Purview sensitivity labels provides layered protection by combining data classification with automated enforcement across Microsoft 365 services.
