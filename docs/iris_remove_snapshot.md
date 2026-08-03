---
title: "Removing Snapshot Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_remove_snapshot.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Snapshot Backups


If you want to detach InterSystems IRIS instance backup data from the application backup policy without deleting the backup files, you can use the Remove from Job operation. When you remove a backup from the job, the backup files remain on the backup repository and continue to be visible in the Veeam Backup & Replication console under Backups > Disk (Orphaned). Veeam Backup & Replication manages detached backups according to the retention period configured for the backup policy. If the policy uses restore-point-based retention, Veeam Backup & Replication does not delete orphaned backups automatically. Delete them manually using the Delete from Disk option.

You can remove snapshot backups from Veeam Backup & Replication in the following ways:

* [Removing Backup from Backup Policy](iris_remove_snapshot_remove_from_policy.md)
* [Remove Backup from Configuration](iris_remove_snapshot_remove_from_configuration.md)
* [Delete Backup from Disk](iris_remove_snapshot_delete.md)

Page updated 2026-07-29

