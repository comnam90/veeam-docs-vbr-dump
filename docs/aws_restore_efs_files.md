---
title: "Performing EFS File-Level Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_efs_files.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing EFS File-Level Restore


You can perform EFS file-level restore only using the backup appliance Web UI. However, you can launch the EFS file-level recovery wizard directly from the Veeam Backup & Replication console. To do that, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the EFS backup policy that protects a file system whose files and folders you want to restore, select the necessary file system and click Amazon EFS file on the ribbon.

Alternatively, you can right-click the file system and select Restore to Amazon EFS files.

Veeam Backup & Replication will open the EFS File-level Recovery wizard in a web browser. Complete the wizard as described in section [Performing File-Level Recovery](aws_restore_item_settings.md).

[![Restore EFS files - Launch](images/aws_restore_efs_files.webp)](images/aws_restore_efs_files.webp "Restore EFS files - Launch")

Page updated 2026-07-20

