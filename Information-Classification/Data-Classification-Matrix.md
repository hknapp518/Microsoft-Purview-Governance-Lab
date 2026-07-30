# Data Classification Matrix

## Overview

Following the data discovery assessment, Knapp Healthcare identified several categories of business information requiring protection through Microsoft Purview.

The following matrix maps business information to the Microsoft Purview sensitivity labels implemented as part of this project.

---

| Business Information | Department | Microsoft Purview Sensitivity Label | Business Justification |
|----------------------|------------|-------------------------------------|------------------------|
| Public Website Content | Marketing | Public | Approved for public distribution |
| Press Releases | Marketing | Information approved for public release | Reviewed and approved for external publication |
| Employee Handbook | Human Resources | Internal information | Intended for internal employees only |
| Employee Personnel Files | Human Resources | Personal (PII) | Contains personally identifiable information |
| Payroll Reports | Human Resources | Confidential – Financial Data | Contains salary and compensation information |
| Budget Reports | Finance | Confidential – Financial Data | Contains confidential financial information |
| Patient Medical Records | Clinical Operations | Confidential – PHI Data | Contains Protected Health Information (PHI) |
| Insurance Claims | Revenue Cycle | Confidential – PHI Data | Contains patient and insurance information |
| Credit Card Payments | Patient Billing | Highly Confidential – PCI Data | Contains payment card information |
| Vendor Contracts | Legal | Internal information | Internal business documentation |

---

## Classification Strategy

Knapp Healthcare will classify information according to business impact, regulatory requirements, and the sensitivity of the data.

Microsoft Purview sensitivity labels provide consistent protection across Microsoft 365 by enabling document classification, encryption, and access controls where appropriate.

The classification matrix serves as the foundation for Data Loss Prevention (DLP), Auto-labeling, and Microsoft Purview Audit policies.
