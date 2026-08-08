---
title: "Backup Files"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup_files.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Files


For every application backup policy for InterSystems IRIS instances, Veeam Backup & Replication creates and stores backup files and a separate metadata file for each backup chain. The backup files provide a consistent and integrated way for Veeam Backup & Replication to store and manage backup data, while ensuring that the data is protected, accessible and can be quickly restored when needed.

All backup files created by the backup policy reside in a dedicated folder in the backup repository. Veeam Backup & Replication creates a set of backup files for each InterSystems IRIS instance in the backup scope.

|  |
| --- |
| NOTE |
| In snapshot-only mode, no backup files are created and no data is transferred to a backup repository. Data is retained as storage snapshots on the storage system. For details, see [Backup Types](iris_backup_types.md). |

Backup Files

Veeam Backup & Replication stores backup files for each InterSystems IRIS instance in the backup scope in the following formats:

* .VBK — full backup file.
* .VIB — incremental backup file.
* .VBM — backup metadata file. It contains information about the InterSystems IRIS instance for which the backup was created, every restore point in the backup chain, how restore points are linked to each other, and so on. The backup metadata file is required for restore operations.

The backup metadata file is updated with every backup policy session.

Page updated 2026-07-24

