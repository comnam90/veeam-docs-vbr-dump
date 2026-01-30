---
title: "Retention of MongoDB Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_retention.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Retention of MongoDB Backups


To set an automatic removal of old backups, you can set the retention policy for MongoDB backups during the application backup policy configuration. After that, Veeam Backup & Replication automatically deletes backup files which are older than specified number of days. For details, see [Storage Settings](mongo_policy_storage.md).

In the storage settings, you can also set the GFS (Grandfather-Father-Son) retention scheme. This scheme allows you to store MongoDB backups for long periods of time — for weeks, months and years. For details, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).

Also, you can manually delete backups from a backup repository using the Veeam Backup & Replication console. For details, see [Deleting Backups Manually Using Veeam Backup & Replication Console](manual_remove.md).


