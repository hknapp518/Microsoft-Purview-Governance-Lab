# Lessons Learned

This project provided hands-on experience designing, testing, troubleshooting, and monitoring Microsoft Purview data protection controls in a Microsoft 365 lab environment.

Rather than focusing only on successful configurations, several of the most valuable lessons came from troubleshooting unexpected behavior and validating how different Microsoft security services interact.

## 1. Start With Classification

Effective DLP depends on accurately identifying the data that needs protection.

Built-in Sensitive Information Types provide broad coverage, but custom Sensitive Information Types allow organizations to detect data that is specific to their environment.

During this project, I created custom SITs using regular expressions, supporting keywords, confidence levels, and character proximity.

One important lesson was that matching a pattern alone is not always enough. Adding contextual evidence can significantly improve detection quality and reduce false positives.

## 2. Simulation Before Enforcement

Testing DLP policies in simulation mode was valuable before enabling enforcement.

Simulation allowed me to validate:

- Sensitive information detection
- External sharing conditions
- Policy matches
- User notifications
- Expected policy behavior

Once the detection logic was validated, the policy could be moved into enforcement with greater confidence.

This reinforced the importance of testing security controls before introducing changes that could affect users or business processes.

## 3. Policy Propagation Matters

Microsoft Purview policy changes are not always immediate.

During testing, I initially expected newly created or modified policies to begin enforcing controls immediately. In several cases, the policy was still synchronizing across Microsoft 365.

This created results that initially appeared to be configuration problems.

The lesson was simple but important:

**Validate policy deployment and synchronization status before troubleshooting deeper technical issues.**

This prevents unnecessary configuration changes and helps isolate the actual cause of unexpected behavior.

## 4. DLP Requires Continuous Tuning

A DLP policy should not be treated as a one-time configuration.

Policies need to be monitored and adjusted based on:

- False positives
- False negatives
- Business workflows
- User impact
- Sensitive information confidence levels
- Alert volume

A technically correct policy can still create operational problems if it generates excessive alerts or interrupts legitimate business activity.

Effective DLP requires balancing security with usability.

## 5. User Communication Is Part of Data Protection

Technical controls alone are not enough.

Policy tips and user notifications provide an opportunity to explain why an action is being blocked and help users understand how sensitive information should be handled.

Clear notifications can turn a blocked action into a security awareness opportunity rather than simply creating frustration for the user.

## 6. Alerts Are More Valuable When Integrated With Security Operations

Purview provides visibility into data security events, but integrating those events with a SIEM provides additional operational value.

In this lab, Microsoft Defender security telemetry was streamed through Azure Event Hub and ingested into Splunk.

This allowed DLP events to become part of the broader security monitoring workflow rather than remaining isolated within the Microsoft Purview portal.

The resulting architecture demonstrated:

**Data Classification → DLP Enforcement → Defender Alert → Azure Event Hub → Splunk**

## 7. Custom Classification Can Support Industry-Specific Use Cases

The BCSI use case demonstrated how Microsoft Purview can be extended to detect organization-specific sensitive information.

A fictional BES Cyber System Information identifier was created using a custom regex pattern and supporting contextual keywords.

That classifier was then connected to a DLP policy designed to prevent external sharing.

The final test successfully demonstrated:

**Custom BCSI SIT → High-Confidence Detection → External Sharing Attempt → DLP Block → Defender Alert → Splunk**

This reinforced how Purview can be adapted to support information protection scenarios relevant to regulated and critical infrastructure environments.

> The BCSI identifier and test data used in this project are fictional lab examples and should not be interpreted as implementing or satisfying a specific NERC CIP compliance requirement.

## 8. Troubleshooting Should Be Methodical

One of the biggest takeaways from the project was the importance of validating assumptions before making configuration changes.

When something did not work as expected, the most effective troubleshooting process was:

1. Confirm the policy is enabled and synchronized.
2. Validate the Sensitive Information Type independently.
3. Confirm the test data actually meets the detection criteria.
4. Verify policy scope and conditions.
5. Check user notifications and enforcement actions.
6. Review Purview and Defender activity.
7. Validate downstream telemetry in Splunk.

This approach helped distinguish configuration problems from propagation delays and expected platform behavior.

## Final Takeaway

The biggest lesson from this project is that data protection is not a single security control.

Effective information protection requires multiple layers working together:

**Identify the data → classify it → apply policy → prevent inappropriate sharing → generate security telemetry → investigate the event.**

Building the complete workflow provided practical experience with both the governance side of Microsoft Purview and the operational security side of Defender, Azure Event Hub, and Splunk.
