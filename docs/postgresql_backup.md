---
title: "PostgreSQL WAL Files Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_backup.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# PostgreSQL WAL Files Backup

In this article

To protect VMs with PostgreSQL instances, you can instruct the backup job to create image-level VM backups and periodically back up write ahead log (WAL) files of PostgreSQL instances. Thus, you will create transactionally consistent backups of PostgreSQL instances that will contain backups of WAL files. If a PostgreSQL instance fails, you can use [Application Item Restore](restore_veeam_explorers.md) to apply WAL files and recover PostgreSQL instances to the necessary state.

Requirements and Limitations

Before you back up WAL files for PostgreSQL instances, consider the following requirements and limitations:

* Veeam Backup & Replication supports log backup and restore for PostgreSQL version 13, 14, 15, 16, 17, 18.
* Veeam Backup & Replication supports only backup of PostgreSQL instances configured on Linux-based VMs.
* Veeam Backup & Replication does not support backup of individual PostgreSQL databases.
* Veeam Backup & Replication does not support high availability cluster configurations and replication setups of PostgreSQL servers.

* Set the archive\_mode parameter to the on mode in PostgreSQL instances.
* The archive\_command and archive\_library parameters must not contain any values in PostgreSQL instances.

* Set the wal\_level parameter to replica or logical in PostgreSQL instances.
* The temporary folder that keeps logs must have enough space and be accessible from Linux guest OS.

* To perform guest processing for PostgreSQL instances on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get an error with the permission denial.

Related Topics

* [WAL Files PostgreSQL Backup Jobs](postgresql_backup_hiw.md)
* [How PostgreSQL WAL Files Backup Works](postgresql_backup_job.md)
* [Retention for PostgreSQL WAL Files](postrgresql_backup_retention.md)
* [Log Shipping Servers](postgresql_log_shipping.md)
* [WAL Backup Statistics](postrgesql_statistics.md)

Page updated 11/12/2025

Page content applies to build 13.0.1.1071
