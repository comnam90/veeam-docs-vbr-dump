---
title: "Backup Types"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_types.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Backup Types


Veeam Backup & Replication using the Veeam Agent for Linux functionality creates consistent backups of MongoDB data. Every backup job session produces a new backup file in the target location. Backup files make up a backup chain. The backup chain can contain files of two types: full backups and incremental backups.

* During the first backup job session, Veeam Backup & Replication performs full backup. It copies all data that you have chosen to back up (entire volumes) and stores the resulting full backup file (.VBK) in the target location. The full backup takes significant time to complete and produces a large backup file: you have to copy the whole amount of data.
* During subsequent backup job sessions, Veeam Backup & Replication performs incremental backups. It copies only new or changed data relative to the last backup job session and saves this data as an incremental backup file (.VIB) in the target location. Incremental backups typically take less time than full backup: you have to copy only changes, not the whole amount of data.

![Backup Types](images/mongo_backup_chain.webp)

For details about backup files that Veeam Backup & Replication creates, see [Backup Files](mongo_backup_files.md).

After several backup cycles, you have a chain of backup files in the target location: the first full backup file and subsequent incremental backup files. Every backup file contains a restore point for backed-up data. A restore point is a "snapshot" of your data at a specific point in time. You can use restore points to roll back your data to the necessary state.

To recover data to a specific restore point, you need a chain of backup files: a full backup file plus a set of incremental backup files following this full backup file. If some file from the backup chain is missing, you will not be able to roll back to the necessary state. For this reason, we recommend that you do not delete separate backup files manually.

![Backup Types](images/mongo_backup_chain_restore_point.webp)

To create backups, you must configure a protection group and an application backup policy, then run the backup process. For details about backup of MongoDB data, see [Working with Application Backup Policy](mongo_policy.md).


