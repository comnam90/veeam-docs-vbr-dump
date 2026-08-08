---
title: "What You Do Next"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_protection_group_after.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# What You Do Next


After you create a protection group, Veeam Backup & Replication automatically rescans ODB servers that you added to the created protection group and deploys Veeam components on these computers. To learn more, see [Rescan Job](iris_rescan_job.md).

After the rescan process completes and Veeam components are successfully deployed on target computers, you can create the application backup policy. To learn more, see [Creating Application Backup Policy](iris_policy_create.md).

If you plan to create the policy in backup mode, make sure at least one Linux-based backup proxy is added to the Veeam Backup & Replication infrastructure as a General-purpose proxy.

Page updated 2026-08-05

