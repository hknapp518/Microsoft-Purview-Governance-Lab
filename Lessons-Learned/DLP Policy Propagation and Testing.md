**DLP Policy Propagation and Testing**

<img width="1530" height="413" alt="image" src="https://github.com/user-attachments/assets/d032ca11-1345-413b-8b96-27dd86207db9" />

During enforcement testing, the Block PHI External Sharing policy was enabled, but an initial external-sharing test did not generate the expected DLP rule match.

Investigation showed that the policy's Policy sync status was still Sync in progress, indicating that the updated configuration had not yet fully propagated across Microsoft 365 workloads.

**Key takeaway**: After creating or modifying Microsoft Purview DLP policies, verify that Policy sync status = Sync completed before performing enforcement validation. Testing while synchronization is still in progress can produce inconsistent results and lead to incorrect conclusions about policy effectiveness.

