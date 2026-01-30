---
title: "Retrying Backup Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_policy_manage_retry.html"
last_updated: "11/27/2024"
product_version: "13.0.1.1071"
---

# Retrying Backup Policy


You can manually retry an application backup policy configured in Veeam Backup & Replication if the policy failed during the previous policy session. When you retry a backup policy, Veeam Backup & Replication processes only those computers in the policy that were not processed successfully during the previous policy session.

To retry a policy:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the application backup policy and click Retry on the ribbon or right-click the policy and select Retry.

[![Retry Application Backup Policy](images/mongo_policy_retry.webp)](images/mongo_policy_retry.webp "Retry Application Backup Policy")


