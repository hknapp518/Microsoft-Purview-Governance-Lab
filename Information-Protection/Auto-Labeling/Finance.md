# Financial Data Auto-Labeling

## Overview

This auto-labeling policy demonstrates how Microsoft Purview can automatically classify financial documents based on built-in Sensitive Information Types.

The policy evaluates files stored in SharePoint and applies the **Confidential – Financial Data** sensitivity label when matching financial information is detected.

## Rule Configuration

Configured Sensitive Information Types include:

- Credit Card Number
- U.S. Bank Account Number
- International Banking Account Number (IBAN)
- SWIFT Code

When the configured conditions are met, Microsoft Purview automatically applies the **Confidential – Financial Data** sensitivity label to the document.

## Protection Flow

**Financial Data → Sensitive Information Type Detection → Auto-Labeling Policy → Confidential – Financial Data**

## Key Takeaway

Auto-labeling reduces reliance on users manually identifying sensitive information and allows classification to drive downstream Information Protection and DLP controls.

## Disclaimer

All financial information and documents used for testing were fictional and created solely for this lab.
<img width="1227" height="644" alt="image" src="https://github.com/user-attachments/assets/509d7a06-5932-43e2-947e-0290bb08de9b" />
