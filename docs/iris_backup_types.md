---
title: "Backup Types"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup_types.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Types


Veeam Backup & Replication uses the unstructured data backup engine to create storage snapshot-based backups of InterSystems IRIS instance data. Depending on the mode configured in the application backup policy, backup sessions produce different types of output. In snapshot-only mode, only storage snapshots are retained on the storage system. In backup mode, every backup policy session produces a new backup file in the target backup repository. Backup files in backup mode make up a backup chain that contains files of two types: full backups and incremental backups.

Snapshot-Only Mode

In snapshot-only mode, Veeam Backup & Replication instructs the storage system to create a storage snapshot of the volumes that hold the InterSystems IRIS instance data. No data is transferred to a backup repository. Snapshots are retained on the storage system according to the snapshot retention settings configured in the policy. You can restore from a storage snapshot, but you cannot restore to a point in time between sessions.

Full Backup

Full backups contain the complete set of InterSystems IRIS instance data. The unstructured data backup engine retrieves the data from the mounted storage snapshot clone and stores the resulting full backup file (.VBK) in the target backup repository. The first backup policy session always produces a full backup.

Incremental Backup

Incremental backups contain only the data that changed since the previous backup. InterSystems IRIS incremental backups use a CBT (Changed Block Tracking) mechanism in the unstructured data backup engine. This functionality enables the processing of only the changed blocks of .DAT files, rather than the entire file, and stores the results as an incremental backup file (.VIB) in the target backup repository. Incremental backups typically take less time and require less storage space than full backups.

The processing of changes in .DAT files differs depending on the Veeam Backup & Replication version:

* Version 13.0.2 and older: The entire .DAT file is processed even when only a single block changed.

* Version 13.1 and newer: Only the changed blocks are transferred and appended to the backup chain.

|  |
| --- |
| NOTE |
| The application backup policy does not process the journal (log) files of the InterSystems IRIS instance. As a result, point-in-time restore is not available. You can restore only to the state captured in a full or incremental backup, or in a storage snapshot. |

After several backup sessions in backup mode, you have a chain of backup files in the target backup repository: the first full backup file and subsequent incremental backup files. Every backup file in the chain contains a restore point with a record of the InterSystems IRIS instance data at the time that backup session ran. You can use restore points to roll back the instance data to the required state.

To recover data to a specific restore point, you need a complete backup chain: a full backup file and all incremental backup files that follow it. If a file in the backup chain is missing, you will not be able to restore to the required state. For this reason, we recommend that you do not delete backup files manually.

For details about the backup files that Veeam Backup & Replication creates, see [Backup Files](iris_backup_files.md).

To create backups, you must configure a protection group and an application backup policy, then run the policy. For details, see [Working with Application Backup Policy](iris_policy.md).

Page updated 2026-07-24

