---
title: "Step 13. Review Backup Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_review_unix.html"
last_updated: "3/30/2026"
product_version: "13.0.1.2067"
---

# Step 13. Review Backup Job Settings


At the Summary step of the wizard, complete the Veeam Agent backup policy configuration process.

1. Review settings of the configured backup policy.
2. Click Finish to close the wizard.

Keep in mind that Veeam Backup & Replication does not apply backup policy to Unix computers immediately. Veeam Agents installed on Unix computers connect to Veeam Backup & Replication every 6 hours and get updated backup policy settings. If you targeted a backup policy at the Veeam backup server and scheduled it earlier than the next connection to Veeam Backup & Replication, this backup policy will get updated backup policy settings at the next backup policy session start.

If you want to apply backup policy immediately, you must synchronize Veeam Agent with Veeam Backup & Replication from the Veeam Agent computer side manually. To learn more, see [Applying Protection Group Configuration to Veeam Agent for Unix](deploy_agent_unix.md#configure).

![Step 13. Review Backup Job Settings](images/agent_policy_summary_unix.webp)


