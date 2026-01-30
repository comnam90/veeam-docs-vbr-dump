---
title: "Performing Active Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_policy_manage_active_full.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Performing Active Full Backup


You can create an ad-hoc full backup — active full backup, and add it to the backup chain on the backup repository. The active full backup resets the backup chain. All subsequent incremental backups use the active full backup as a starting point. The previously used full backup will remain on the backup repository until it is removed from the backup chain according to the retention job.

When you start active full backup for a backup policy, Veeam Backup & Replication does not check whether connection to computers is active at the time when the command is sent. Keep in mind that the active full backup operation will be performed only on those computers that received the command from the backup server.

To perform active full backup on computers added to the backup policy:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the backup policy and click Active Full on the ribbon or right-click the policy and select Active full. After that, confirm the backup policy start.

[![Perform Active Full Backup](images/mongo_policy_active_full.webp)](images/mongo_policy_active_full.webp "Perform Active Full Backup")


