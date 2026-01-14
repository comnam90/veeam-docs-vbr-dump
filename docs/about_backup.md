---
title: "About Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/about_backup.html"
last_updated: "2/10/2025"
product_version: "13.0.1.1071"
---

# About Backup

In this article

Veeam Backup & Replication is built for virtual environments. It operates at the virtualization layer and uses an image-based approach for VM backup.

Veeam Backup & Replication does not install agent software inside the VM guest OS to retrieve VM data. To back up VMs, it leverages VMware vSphere snapshot capabilities. When you back up a VM, Veeam Backup & Replication requests VMware vSphere to create a VM snapshot. You can think of the VM snapshot as a point-in-time copy of a VM that includes virtual disks, system state, configuration, and so on. Veeam Backup & Replication uses this point-in-time copy as a data source for backup.

Veeam Backup & Replication copies VM data from the source datastore at a block level. It retrieves VM data, compresses and deduplicates it, and stores in backup files in the backup repository in Veeam proprietary format.

In Veeam Backup & Replication, backup is a job-driven process. To perform backup, you need to configure backup jobs. A backup job is a configuration unit of the backup activity. The backup job defines when, what, how and where to back up. One backup job can be used to process one or several VMs. You can instruct Veeam Backup & Replication to run jobs automatically by schedule or start them manually.

The first backup job session always produces a full backup of the VM image. Subsequent backup job sessions are incremental — Veeam Backup & Replication copies only those data blocks that have changed since the last backup job session. To keep track of changed data blocks, Veeam Backup & Replication uses different approaches. For more information, see [Changed Block Tracking](changed_block_tracking.md).

In This Section

* [How Backup Works](backup_hiw.md)
* [Backup Infrastructure for Backup](backup_architecture.md)
* [Backup Chain](backup_files.md)
* [Changed Block Tracking](changed_block_tracking.md)
* [Data Compression and Deduplication](compression_deduplication.md)
* [Data Exclusion](data_exclusion.md)
* [VMware Tools Quiescence](tools_quiescence.md)
* [Guest Processing](guest_processing.md)
* [Microsoft SQL Server Log Backup](sql_backup.md)
* [Oracle Log Backup](oracle_backup.md)
* [PostgreSQL WAL Files Backup](postgresql_backup.md)
* [Backup Job Scheduling](scheduling.md)
* [Immutability for Backup Files](immutability.md)
* [Health Check for Backup Files](backup_health_check.md)
* [Compact of Full Backup File](backup_compact_file.md)
* [Backup Move](backup_moving.md)
* [Resume on Disconnect](replica_resume_disconnect.md)
* [Snapshot Hunter](snapshot_hunter.md)

Page updated 2/10/2025

Page content applies to build 13.0.1.1071
