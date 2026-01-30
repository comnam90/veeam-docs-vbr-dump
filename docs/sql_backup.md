---
title: "Microsoft SQL Server Log Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sql_backup.html"
last_updated: "6/25/2024"
product_version: "13.0.1.1071"
---

# Microsoft SQL Server Log Backup


To protect Microsoft SQL Server VMs, you can instruct the backup job to create image-level VM backups and periodically back up database transaction logs. If Microsoft SQL Server fails, you can restore the Microsoft SQL Server VM from the necessary restore point of the image-level backup. Afterward, you can use Veeam Explorer for Microsoft SQL Server to apply transaction logs and get databases on the Microsoft SQL Server to the necessary state between backups.

Related Topics

* [Transaction Log Backup Jobs](sql_backup_job.md)
* [How Microsoft SQL Server Log Backup Works](sql_backup_hiw.md)
* [Retention for Transaction Log Backups](sql_backup_retention.md)
* [Log Shipping Servers](sql_backup_log_shipping.md)
* [Transaction Log Backup Statistics](sql_backup_stats.md)
* [Support for Always On Availability Groups](alwayson_support.md)


