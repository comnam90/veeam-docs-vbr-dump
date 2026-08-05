---
title: "Performing Active Full Backup Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performing_active_full_backup_hv_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Active Full Backup Using Web UI


You can create an ad-hoc full backup — active full backup, and add it to the backup chain in the backup repository. The active full backup resets the backup chain. All subsequent incremental backups use the active full backup as a starting point. The previously used full backup will remain in the backup repository until it is removed from the backup chain according to the retention policy.

Performing Active Full Backup for All Workloads

To perform active full backup for all workloads in a backup job:

1. Open Jobs node in the management pane.
2. In the working area, right-click the necessary job and select Active Full.

[![Perform active full backup using web ui](images/create_active_full_hv_web.webp)](images/create_active_full_hv_web.webp "Perform active full backup using web ui")

Page updated 2026-06-29

