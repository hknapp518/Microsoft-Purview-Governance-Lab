# Payroll Protection Policy

## Business Problem

Knapp Healthcare experienced an incident where an employee in Human Resources accidentally emailed a payroll spreadsheet containing employee salary information to an external recipient.

This event highlighted the need to prevent unauthorized sharing of sensitive financial information while allowing authorized business operations to continue.

---

## Business Objective

Implement a Microsoft Purview Data Loss Prevention (DLP) policy that protects payroll information from accidental disclosure.

---

## Scope

**Locations**

- Exchange Online
- SharePoint Online
- OneDrive for Business

---

## Sensitive Information Types

The policy monitors for:

- Social Security Numbers (SSNs)
- Banking information
- Salary and compensation information
- Tax identification numbers

---

## Policy Actions

When sensitive payroll information is detected:

- Block external sharing
- Display a policy tip to the user
- Notify the user of the policy violation
- Generate an audit event
- Alert the Security Administrator

---

## Expected Business Outcome

The Payroll Protection Policy reduces the risk of accidental disclosure of employee financial information while supporting compliance with organizational security policies.

---

## Implementation Note

This policy is designed as part of the Microsoft Purview implementation for Knapp Healthcare and aligns with the organization's information protection strategy.
