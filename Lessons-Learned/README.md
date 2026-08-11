# Lessons Learned

Building this lab reinforced that effective data protection requires more than creating a DLP policy. Classification, testing, enforcement, troubleshooting, and security monitoring all need to work together.

## Classification Drives Everything

DLP is only as effective as the classification behind it.

Built-in Sensitive Information Types provide broad coverage, while custom SITs can identify organization-specific data using regex, contextual evidence, confidence levels, and proximity.

Testing the classifier independently before connecting it to DLP made troubleshooting much easier and helped reduce false positives.

## Test Before Enforcing

Simulation mode was valuable for validating detection logic, policy scope, external-sharing conditions, notifications, and expected behavior before enabling enforcement.

This also highlighted the importance of continuous tuning. A technically correct policy can still create problems if it generates excessive alerts or interferes with legitimate workflows.

**Simulate → Validate → Tune → Enforce**

## Account for Policy Propagation

Purview policy changes are not always immediate.

During testing, propagation delays sometimes appeared to be configuration failures. Before changing a policy, I learned to verify deployment and synchronization status first.

A reliable troubleshooting sequence became:

1. Confirm policy status and synchronization.
2. Test the Sensitive Information Type independently.
3. Validate the test data and detection criteria.
4. Verify policy scope, conditions, and actions.
5. Review Purview and Defender activity.
6. Confirm downstream telemetry.

## Connect Data Protection to Security Operations

Blocking sensitive data is only part of the process. The resulting security activity also needs to reach the analysts responsible for investigation.

In this lab, DLP alerts were validated in Microsoft Defender XDR, streamed through Azure Event Hubs, and ingested into Splunk.

**Data Classification → DLP Enforcement → Defender XDR → Azure Event Hubs → Splunk**

The BCSI scenario brought these pieces together by using a custom classifier to identify fictional organization-specific information, prevent external sharing, generate an alert, and validate the resulting telemetry in the SIEM.

## Final Takeaway

The biggest lesson was to treat data protection as a lifecycle rather than a single control:

**Identify → Classify → Protect → Monitor → Investigate → Tune**

Building each stage separately made it easier to understand where failures occurred and how Microsoft Purview fits into the broader security operations workflow.

## Disclaimer

All organizations, users, identifiers, and sensitive data used in this project are fictional and were created solely for lab testing.

The BCSI scenario is NERC CIP-inspired and does not represent or claim compliance with a specific NERC CIP requirement.
