# Sensitivity Label Policy

## Purpose

Sensitivity Label Policies determine which Microsoft Purview sensitivity labels are published to users and how those labels are applied throughout the organization.

For Knapp Healthcare, label policies are designed to provide users with the appropriate classification options based on their business responsibilities while maintaining consistent information protection.

---

## Label Policy Design

The following label policies are implemented as part of the Microsoft Purview deployment.

| Label Policy | Intended Users | Purpose |
|--------------|----------------|---------|
| Public & Internal Labels | All Employees | Provides users with labels for information intended for internal use or approved public distribution. |
| Sensitive Labels | Human Resources, Finance, Clinical Operations, Legal | Provides access to labels used to classify highly sensitive business, financial, and healthcare information. |
| Organization Label Policy | Enterprise-wide | Publishes the approved sensitivity label taxonomy across Microsoft 365 applications. |

---
<img width="1593" height="611" alt="image" src="https://github.com/user-attachments/assets/f69eaa24-d892-41bd-bd27-0ec9badcdb9a" />

## Business Justification

Separating label policies allows Knapp Healthcare to:

- Simplify label selection for employees.
- Reduce classification errors.
- Restrict highly sensitive labels to departments that manage regulated data.
- Maintain a consistent information protection strategy across Microsoft 365.

---

## Expected Outcome

By implementing label policies, Knapp Healthcare ensures that employees receive only the labels appropriate for their role while supporting compliance, information governance, and data protection objectives.

---

## Implementation Note

This design is based on Microsoft Purview sensitivity label policies configured within a Microsoft 365 lab environment and adapted to the Knapp Healthcare implementation scenario.
