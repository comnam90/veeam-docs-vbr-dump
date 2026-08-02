---
title: "Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Retention


To automatically remove outdated restore points, configure a retention policy when you create the application backup policy. At the Storage step, in the Retention Policy field, specify the number of days for which Veeam Backup & Replication keeps backup files in the target backup repository (7 days by default). After this period, Veeam Backup & Replication removes the earliest restore points from the backup chain. For details, see [Step 4. Specify Storage Settings](iris_policy_storage.md).

To retain full backups for longer periods — weeks, months or years — enable the Grandfather-Father-Son (GFS) retention scheme in the storage settings of the policy. For details, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).

In addition to backup files, you can retain storage snapshots on the storage system. Select the Retain storage snapshots option in the storage settings and specify how many days to keep them. You can also make the snapshots immutable so that they cannot be modified or deleted during the retention period.

In snapshot-only mode, Veeam Backup & Replication does not create backup files in a repository. It retains only storage snapshots on the storage system according to the snapshot retention settings. The days-based retention policy and the GFS scheme do not apply in this mode.

You can also remove InterSystems IRIS instance backups manually in the Veeam Backup & Replication console. For details, see [Removing Backups](iris_remove_backup.md) and [Removing Snapshot Backups](iris_remove_snapshot.md).

Page updated 2026-07-15

