---
title: "Performing RDS Database Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_performing_rds_database_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing RDS Database Restore


In case of a disaster, you can restore corrupted databases of Microsoft SQL Server and PostgreSQL DB instances from an image-level backup. Veeam Plug-in for AWS allows you to restore one or more databases of only one DB instance at a time, to the original location or to a new location.

|  |
| --- |
| Important |
| [Applies only to Microsoft SQL Server DB instances] Veeam Plug-in for AWS does not support restoring databases that contain the FILESTREAM file group. |

To restore databases of a protected DB instance, do the following:

1. [Launch the Database Restore wizard](aws_restore_rds_database_launch.md).
2. [Select databases](aws_restore_rds_database_point.md).
3. [Specify account settings for restore](aws_restore_rds_database_workers.md).
4. [Specify data retrieval settings for archived backups](aws_data_retrieval_database.md).
5. [Configure target instance settings](aws_restore_rds_database_settings.md).
6. [Specify a restore reason](aws_restore_rds_database_reason.md).
7. [Finish working with the wizard](aws_restore_rds_database_finish.md).

Page updated 2026-05-22

