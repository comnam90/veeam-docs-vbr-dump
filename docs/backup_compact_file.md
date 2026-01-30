---
title: "Compact of Full Backup File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_compact_file.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Compact of Full Backup File


The backup job constantly transforms the full backup file in the backup chain to meet retention policy settings. This transformation process, however, has a side effect. Over time, the full backup file becomes large and fragmented. Consequently, operations of reading and writing data from and to the backup file slow down.

To resolve this problem, Veeam Backup & Replication allows you to defragment and compact the full backup file periodically. During the file compact operation, Veeam Backup & Replication creates a new full backup file in the target repository: it copies existing data blocks from the old backup file, rearranges and stores them close to each other. As a result, the full backup file gets defragmented, its size reduced, and the speed of reading and writing from and to the file increases.

To compact the full backup file periodically, you must enable the Defragment and compact full backup file option in the backup job settings and define the compact operation schedule. By default, the compact operation is performed on the last Saturday of every month. You can change the compact operation schedule and instruct Veeam Backup & Replication to perform it weekly or monthly on specific days.

![Compact of Full Backup File](images/backup_job_defragment.webp)

Limitations for Full Backup File Compact

The full backup file compact has the following limitations:

* The Defragment and compact full backup file option works for forever forward incremental backup chains or reverse incremental backup chains (deprecated). For this reason, you must not schedule active or synthetic full backups.

Although you do not schedule active full backups for forever forward incremental backup chains or reverse incremental backup chains (deprecated), you can create full backups. For example, you can create them manually or Veeam Backup & Replication can create them during the health check. On the day when active full backups are triggered, Veeam Backup & Replication does not create compact full backups. Veeam Backup & Replication will create them on another day during the backup job session.

* Veeam Backup & Replication does not compact full backup files that have been offloaded to cloud-based object storage. For more information, see [Capacity Tier](capacity_tier.md).
* The backup repository must have enough space to store a file of the full backup size. During the compact process, Veeam Backup & Replication creates auxiliary files that exist in the backup repository until the end of the compact operation.
* [For per-machine backup chains] If you add a new VM to an existing backup job that has been run for some time, Veeam Backup & Replication will perform the compact full operation for it during the next incremental backup job session for the added VM.
* If you change the block size in the backup job settings, Veeam Backup & Replication does not change the block size in the compacted backup file till the next full backup. However, if you change compression settings in the backup job settings, during the next compact file operation, Veeam Backup & Replication changes the compression level for the compacted backup file.

Removal of Deleted VMs Data

During the compact operation, Veeam Backup & Replication does not copy all data blocks from the VBK file to the newly created file. It copies only data blocks of VMs whose information is stored in the configuration database. For example, if the VM is removed from the backup job, its data is not copied to the new full backup file. This approach helps reduce the size of the full backup file and remove unnecessary data from it.

VM Data Take Out

If the full backup file contains data for a VM that has only one restore point and this restore point is older than 7 days, during the compact operation, Veeam Backup & Replication will extract data for this VM from the full backup file and write this data to a separate full backup file. Such backup will be displayed under the Backups > Disk (Imported) node in the Home view.

The mechanism works if the following conditions are met:

* The Remove deleted VMs data option is not enabled in the backup job settings.
* The Use per-machine backup files option is not enabled in backup repository settings.

Related Topics

[Creating Backup Jobs](backup_job.md)


