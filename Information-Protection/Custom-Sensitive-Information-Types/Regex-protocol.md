# Clinical Protocol Identifier

## Overview

This Custom Sensitive Information Type (SIT) was created to identify organization-specific clinical research protocol identifiers that are not covered by Microsoft Purview's built-in Sensitive Information Types.

The scenario uses fictional clinical research data created specifically for this lab.

## Detection Logic

The custom SIT uses a regular expression to identify protocol numbers that follow the organization's fictional naming convention.

### Regular Expression

```regex
\b(KNAPP-PROT-\d{4}-\d{3})\b
```

Example identifier:

```text
KNAPP-PROT-2026-001
```

## Regex Configuration

The regex was configured as a **String match** within the custom Sensitive Information Type.

<img width="802" height="880" alt="image" src="https://github.com/user-attachments/assets/5bc38ee3-193a-443c-b75b-c11ad2cfd31b" />

## Validation

The custom SIT was tested against a fictional clinical research document containing:

```text
KNAPP-PROT-2026-001
```

Microsoft Purview successfully detected the identifier during testing.

<img width="698" height="739" alt="image" src="https://github.com/user-attachments/assets/4a4c97e5-75c5-4e0c-9e66-c8c55b0c209f" />

**Regex Pattern → Custom SIT Match → DLP Policy**

The custom SIT was later used by the **Protect Clinical Research Protocols** DLP policy to identify organization-specific protocol information during external-sharing tests.

## Key Takeaway

Custom Sensitive Information Types allow organization-specific naming conventions to become enforceable data-classification signals in Microsoft Purview.

Testing the regex independently also helps validate detection before connecting the classifier to a DLP policy.

## Disclaimer

The organization, protocol identifiers, documents, and data used in this scenario are fictional and were created solely for lab testing.


