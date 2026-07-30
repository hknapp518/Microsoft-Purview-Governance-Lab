# Data Inventory

## Overview

As part of the Microsoft Purview implementation, Knapp Healthcare conducted a data discovery exercise to identify the organization's sensitive information and determine the appropriate level of protection.

---

## Data Classification Inventory

| Department | Data Type | Examples | Sensitivity |
|------------|-----------|----------|-------------|
| Human Resources | Employee Records | Personnel files, performance reviews | Confidential |
| Human Resources | Payroll | Salary information, tax forms, direct deposit | Highly Confidential |
| Finance | Financial Reports | Budgets, quarterly reports, invoices | Confidential |
| Finance | Accounts Payable | Vendor invoices, banking information | Confidential |
| Clinical Operations | Patient Records | Medical history, diagnoses, treatment plans | Highly Confidential |
| Clinical Operations | Insurance Information | Claims, member IDs, billing records | Highly Confidential |
| Clinical Research | Research Documents | Clinical trial protocols, participant data | Confidential |
| Legal | Contracts | Vendor agreements, employment contracts | Confidential |
| Information Technology | System Documentation | Network diagrams, server inventories | Internal |
| Administration | Employee Handbook | Company policies and procedures | Internal |

---

## High-Risk Data Types

The following information requires the highest level of protection:

- Protected Health Information (PHI)
- Social Security Numbers (SSNs)
- Payroll and salary information
- Banking information
- Credit card numbers
- Clinical research participant data

---

## Microsoft Purview Impact

This inventory will be used to:

- Design the Sensitivity Label taxonomy.
- Develop Data Loss Prevention (DLP) policies.
- Configure Auto-labeling policies.
- Define audit monitoring requirements.
- Support incident investigations.
