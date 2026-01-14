---
title: "Oracle Log Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_backup.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---

# Oracle Log Backup

In this article

Veeam Backup & Replication supports backup of Oracle database archived logs and restore of Oracle databases.

Database archived logs are created by the Oracle system. The Oracle database can run in one of the following logging modes:

* ARCHIVELOG — logs are saved and can be used for recovery purposes.
* NOARCHIVELOG — no logs are saved. This mode is not recommended as it does not provide proper disaster recovery.

With ARCHIVELOG mode enabled, the Oracle system stores database archived logs in a certain location on the VM guest OS, as specified by the database administrator. Veeam Backup & Replication allows you to set up the following ways of log handling:

* Instruct the backup job to collect log files from the Oracle VM and ship them to the backup repository, where they are stored next to image-level backups of the Oracle VM.
* Skip log processing — log files remain untouched on the Oracle VM and are preserved within the image-level backup.

If you enable application-aware processing for an Oracle VM, during the job session Veeam Backup & Replication installs non-persistent runtime components or uses (if necessary, installs) persistent agent components on this VM to collect information about the database and process archived logs according to job settings. Application-specific settings are configured at the Guest Processing step of the backup job wizard — you can specify how logs should be backed up and deleted for Oracle databases.

Requirements for Archived Log Backup

* Veeam Backup & Replication supports archived log backup and restore for Oracle Database version 11 and later. Oracle Database may run on a Microsoft Windows VM or Linux VM.
* Automatic Storage Management (ASM) is supported for Oracle Database 11 and later.
* Oracle Database Express Edition (XE) is supported if running on Microsoft Windows machines only.

Related Topics

* [Archived Log Backup Jobs](oracle_backup_job.md)
* [How Oracle Archived Log Backup Works](oracle_backup_hiw.md)
* [Retention for Archived Log Backup](oracle_backup_retention.md)
* [Log Shipping Servers](oracle_log_shipping.md)
* [Archived Log Backup Statistics](oracle_statistics.md)

Page updated 3/4/2025

Page content applies to build 13.0.1.1071
