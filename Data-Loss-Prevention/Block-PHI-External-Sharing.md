# Block PHI External Sharing

## Overview

This DLP policy was created to prevent external sharing of content classified with the **Confidential – PHI Data** sensitivity label.

The policy protects sensitive healthcare information across supported Microsoft 365 locations.

## Policy Configuration

| Setting | Configuration |
| --- | --- |
| Policy Name | Block PHI External Sharing |
| Protected Label | Confidential – PHI Data |
| Locations | Exchange Online, SharePoint Online, OneDrive |
| Policy Mode | Enabled |

## Policy Logic

The policy detects content classified with the **Confidential – PHI Data** sensitivity label and applies restrictions when that content is shared outside the organization.

This connects sensitivity labeling with DLP enforcement so classification can drive data-protection controls across Microsoft 365.

## Validation

The policy was tested using fictional healthcare data in a controlled external-sharing scenario.

Testing confirmed that the PHI sensitivity label could be used by the DLP policy to identify protected content and enforce the configured external-sharing restriction.

**PHI Sensitivity Label → External Sharing Condition → DLP Match → Protection**

## Key Takeaway

Sensitivity labels can provide classification context that DLP policies use to enforce protection consistently across Microsoft 365.

## Disclaimer

All healthcare information, users, recipients, and organizations used in this scenario are fictional and were created solely for lab testing.

<img width="598" height="809" alt="image" src="https://github.com/user-attachments/assets/30b6f809-441f-43a6-9a73-88e147b56a47" />
<img width="1227" height="713" alt="image" src="https://github.com/user-attachments/assets/1fc7e6b9-60af-4df3-b782-1196f44a3667" />

<img width="1875" height="896" alt="image" src="https://github.com/user-attachments/assets/d5681b34-9126-4ed7-b5a2-370c7efefe52" />
Figure: Microsoft Defender incident automatically generated from the Purview DLP policy match, showing the correlated user, alert, activity, and Exfiltration classification.
