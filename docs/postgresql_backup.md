---
title: "PostgreSQL WAL Files Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# PostgreSQL WAL Files Backup


To protect VMs with PostgreSQL instances, you can instruct the backup job to create image-level VM backups and periodically back up write ahead log (WAL) files of PostgreSQL instances. Thus, you will create transactionally consistent backups of PostgreSQL instances that will contain backups of WAL files. If a PostgreSQL instance fails, you can use [Application Item Restore](restore_veeam_explorers.md) to apply WAL files and recover PostgreSQL instances to the necessary state.

Requirements and Limitations

Before you back up WAL files for PostgreSQL instances, consider the following requirements and limitations:

* Veeam Backup & Replication supports log backup and restore for PostgreSQL version 14, 15, 16, 17, 18.
* Veeam Backup & Replication supports backup of PostgreSQL instances configured on both Linux-based and Microsoft Windows-based VMs.
* Veeam Backup & Replication supports backup of PostgreSQL clusters managed by Patroni 4.0.6 or later.
* Veeam Backup & Replication does not support backup of individual PostgreSQL databases.

* Set the archive\_mode parameter to the on mode in PostgreSQL instances.
* The archive\_command and archive\_library parameters must not contain any values in PostgreSQL instances.

* Set the wal\_level parameter to replica or logical in PostgreSQL instances.
* The temporary folder that keeps logs must have enough space and be accessible from Linux guest OS.

* To perform guest processing for PostgreSQL instances on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get an error with the permission denial.

If you plan to back up PostgreSQL clusters managed by Patroni, consider the following:

* The patronictl utility must be installed on all cluster nodes.
* For each cluster node added to the backup job, specify guest OS and database credentials, in the same way as for standalone PostgreSQL instances.
* Veeam Backup & Replication backs up WAL files from the leader node of the cluster only. Add all nodes that can become the leader node to the backup job — otherwise, Veeam Backup & Replication cannot back up WAL files if the leader node changes.
* It is recommended that you configure the same application-aware processing settings for all cluster nodes.

Related Topics

* [WAL Files PostgreSQL Backup Jobs](postgresql_backup_hiw.md)
* [How PostgreSQL WAL Files Backup Works](postgresql_backup_job.md)
* [Retention for PostgreSQL WAL Files](postgresql_backup_retention.md)
* [Log Shipping Servers](postgresql_log_shipping.md)
* [WAL Backup Statistics](postgresql_statistics.md)

Page updated 2026-07-28

