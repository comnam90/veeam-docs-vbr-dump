---
title: "Database Protection"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_protection.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Database Protection

In this article

After you configure Veeam Plug-In, you can use the Oracle RMAN functionality to back up databases. Veeam Plug-In will automatically transfer the backup files to the Veeam backup repository. For more information about configuring Veeam Plug-In, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md).

The examples given below are for demonstration purposes only. The backup process is performed on the Oracle RMAN side. Consider configuring required RMAN-specific parameters that may affect the backup process. For details on the backup functionality of Oracle RMAN, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmbckba.htm).

|  |
| --- |
| Note |
| Consider the following:   * In the Veeam Plug-In configuration wizard, you can enable/disable Veeam Plug-In [Data Compression and Deduplication](compression_deduplication.md). If you enable the Veeam Plug-In compression, do not use Oracle RMAN integrated compression as well. It can slow down the backup and restore processes. * It is Oracle's best practice to add the EXIT; command at the bottom of the script to shut down the RMAN utility. Without the EXIT; command in the script, it is up to Oracle RMAN to decide when to close the backup session, which can lead to multiple unclosed RMAN backup sessions. * Backups created by Veeam Plug-Ins cannot be used as a source for file to tape or backup to tape jobs. |

|  |
| --- |
| Tip |
| If you have configured the retention policy, run the DELETE OBSOLETE command after the database backup to delete obsolete backups from the repository. |

In this Section

* [Oracle RMAN Full Backup](rman_backup.md)
* [Oracle RMAN Channel Allocation](rman_allocation_backup.md)
* [Backup Job in Veeam Backup & Replication](rman_job_vbr.md)

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
