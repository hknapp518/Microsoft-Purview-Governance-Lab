## Rule Configuration

The SharePoint auto-labeling rule inspects files stored within SharePoint document libraries for built-in Microsoft Purview Sensitive Information Types.

Configured detections include:

- Credit Card Number
- U.S. Bank Account Number
- International Banking Account Number (IBAN)
- SWIFT Code

When these conditions are met, Microsoft Purview automatically applies the **Confidential – Financial Data** sensitivity label to the document.

This automatic classification enables downstream Information Protection and Data Loss Prevention (DLP) policies to enforce security controls without requiring manual user classification.
<img width="1227" height="644" alt="image" src="https://github.com/user-attachments/assets/509d7a06-5932-43e2-947e-0290bb08de9b" />
