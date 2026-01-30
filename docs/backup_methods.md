---
title: "Backup Methods"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_methods.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Backup Methods


Veeam Backup & Replication provides the following methods for creating backup chains:

* Forever forward incremental (FFI)

When the forever forward incremental (FFI) backup method is used, Veeam Backup & Replication creates a backup chain that consists of the first full backup file (VBK) and a set of forward incremental backup files (VIBs) following it.

This backup method helps you save space on the backup storage because Veeam Backup & Replication stores only one full backup file and removes incremental backup files once the [retention period is exceeded](retention_forever_incremental.md). To meet retention policy settings, Veeam Backup & Replication injects data of an incremental file into the full backup file before deleting the increment. Such transformations can lead to the fragmentation of the full backup file, and you have to schedule the [compact of full backup file](backup_compact_file.md) operation. This operation produces an additional I/O load on the backup storage. Overall, the FFI method produces a moderate I/O impact on the backup storage compared to other backup methods.

Restore to the earliest restore point from backup files created using the FFI method is the fastest compared to other methods because the first available restore point is always a full backup. Restore to other restore points can be compared by speed with the FI method.

For more information on the FFI backup method and how it works, see [Forever Forward Incremental Backup](incremental_forever_backup.md).

![Backup Methods](images/forward_incremental.webp)

* Forward incremental (FI)

When the forward incremental (FI) backup method is used, Veeam Backup & Replication creates a backup chain that consists of multiple full backup files (VBKs) and sets of forward incremental backup files (VIBs) following each full backup file. Full backups can be created using [synthetic full](synthetic_full_backup.md) and [active full](active_full_backup.md) methods. By doing regular full backups, the backup chain is split into shorter series. This lowers the chances of losing the backup chain completely and makes this backup method the most reliable.

This backup method requires more storage space than other methods because the backup chain contains multiple full backup files, and sometimes Veeam Backup & Replication stores more restore points than specified in the retention policy settings due to the specifics of the FI retention policy. For more information on how backups are retained, see [Forward Incremental Backup Retention Policy](retention_incremental.md).

The FI backup method produces the lowest I/O impact on the backup storage. However, the impact on the backup storage increases on days when synthetic full backups are scheduled; the impact on the production storage increases on days when active full backups are scheduled.

Restore from backup files created using the FI method is the most optimal in time compared to other methods (in cases when you do not restore to the earliest or latest restore point). That is because the backup chain is usually divided into short series of full backup files and incremental files, and the aggregation of the desired restore point does not take a long time.

For more information on the FI backup method and how it works, see [Forward Incremental Backup](forward_incremental_backup.md).

![Backup Methods](images/forward_incremental_chain.webp)

* Reverse incremental (RI) (Deprecated)

|  |
| --- |
| Important |
| For backup jobs created in Veeam Backup & Replication versions prior to 13, you could enable the Reverse Incremental backup mode. In Veeam Backup & Replication version 13, this option is deprecated, and you cannot select it for new jobs. However, backup jobs created in earlier versions with Reverse Incremental backup mode enabled will continue to work after upgrading to Veeam Backup & Replication version 13. |

When the reverse incremental (RI) backup method is used, Veeam Backup & Replication creates a backup chain that consists of the full backup file (VBK) and a set of reverse incremental backup files (VRBs) preceding it.

This backup method helps you save space on the backup storage because Veeam Backup & Replication stores only one full backup file (if you do not schedule periodic full backups) and removes incremental backup files once the [retention period is exceeded](reversed_incremental_backup.md). For more information on how backups are retained, see [Reverse Incremental Backup](reversed_incremental_backup.md).

The RI method produces the heaviest I/O impact on the backup storage compared to other backup methods. That is because, during backup, Veeam Backup & Replication injects changed data blocks into the full backup file and also creates reverse incremental backup files. Such transformations can lead to the fragmentation of the full backup file, and you have to schedule the [compact of full backup file](backup_compact_file.md) operation. This operation produces an additional I/O load on the backup storage.

Restore to the latest restore point from backup files created using the RI method is the fastest compared to other methods because the most recent restore point is always a full backup and gets updated after every backup cycle. Restore to earlier restore points is slower than for other backup methods.

For more information on the RI backup method and how it works, see [Reverse Incremental Backup](reversed_incremental_backup.md).

![Backup Methods](images/reversed_incremental.webp)

Related Topics

* [Switching Between Backup Methods](switching_between_methods.md)
* [Active Full Backup](active_full_backup.md)
* [Synthetic Full Backup](synthetic_full_backup.md)
* [Short-Term Retention Policy](retention_policy.md)
* [Backup Chain Formats](per_vm_backup_files.md)
* [Creating Backup Jobs](backup_job.md)


