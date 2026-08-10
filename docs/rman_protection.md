---
title: "Database Protection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_protection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Database Protection


After you configure Veeam Plug-In, you can use the Oracle RMAN functionality to back up databases. Veeam Plug-In will automatically transfer the backup files to the Veeam backup repository. For more information about configuring Veeam Plug-In, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md).

The examples given below are for demonstration purposes only. The backup process is performed on the Oracle RMAN side. Consider configuring required RMAN-specific parameters that may affect the backup process. For details on the backup functionality of Oracle RMAN, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmbckba.htm).

Before you start you start protecting your Oracle database Veeam Plug-In, review [Considerations and Limitations](rman_limitations.md).

|  |
| --- |
| Tip |
| If you have configured the retention policy, run the DELETE OBSOLETE command after the database backup to delete obsolete backups from the repository. |

In this Section

* [Oracle RMAN Full Backup](rman_backup.md)
* [Oracle RMAN Channel Allocation](rman_allocation_backup.md)
* [Backup Job in Veeam Backup & Replication](rman_job_vbr.md)

Page updated 2026-07-10

