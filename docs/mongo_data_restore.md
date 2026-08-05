---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_data_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Restore


With Veeam Backup & Replication, you can restore MongoDB instances or collections from backups that reside on Veeam backup repositories. You can restore to the original location or another server. You can also restore from a backup copy based on MongoDB backups.

If you have backed up database logs, you can perform point-in-time recovery. For details on the log backup, see [Oplog Backup](mongo_oplog_backup.md).

Restore operations are performed on the Veeam Backup & Replication side. For restore, Veeam Backup & Replication uses the functionality of Veeam Explorer for MongoDB. For details, see [Restoring with Veeam Explorer for MongoDB](mongo_restore.md).

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

Page updated 2026-07-30

