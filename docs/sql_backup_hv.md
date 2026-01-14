---
title: "Microsoft SQL Server Log Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sql_backup_hv.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Microsoft SQL Server Log Backup

In this article

To protect Microsoft SQL Server VMs, you can instruct the backup job to create image-level VM backups and periodically back up database transaction logs. If Microsoft SQL Server fails, you can restore the Microsoft SQL Server VM from the necessary restore point of the image-level backup. Afterward, you can use Veeam Explorer for Microsoft SQL Server to apply transaction logs and get databases on the Microsoft SQL Server to the necessary state between backups.

Related Topics

* [Transaction Log Backup Jobs](sql_backup_job_hv.md)
* [How Microsoft SQL Server Log Backup Works](sql_backup_hiw_hv.md)
* [Retention for Transaction Log Backups](sql_backup_retention_hv.md)
* [Log Shipping Servers](sql_backup_log_shipping_hv.md)
* [Transaction Log Backup Statistics](sql_backup_stats_hv.md)
* [Support for Always On Availability Groups](alwayson_support_hv.md)

Page updated 2/11/2025

Page content applies to build 13.0.1.1071
