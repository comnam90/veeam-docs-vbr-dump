---
title: "Restoring Configuration Database on Windows-Based Backup Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_restore.html"
last_updated: "11/9/2025"
product_version: "13.0.1.1071"
---

# Restoring Configuration Database on Windows-Based Backup Server

In this article

Restore of the configuration database is helpful in the following situations:

* The configuration database got corrupted and you want to recover data from the configuration backup.
* You want to deploy the configuration database on a new Microsoft SQL Server or PostgreSQL and restore data from the configuration backup to it.
* You want to roll back the configuration database to a specific point in time.
* You want to restore data to a new configuration database on the same database instance, for example, for testing purposes.

You can restore a configuration backup on the same backup server where the backup was created or on another backup server.

|  |
| --- |
| Note |
| If you use cloud plug-ins to protect VMs in AWS, Microsoft Azure and other environments and want to restore cloud backup server configurations, see the following guides:   * Google Cloud, the [Configuration Restore](https://helpcenter.veeam.com/docs/vbgc/guide/performing_configuration_restore.html?ver=7) section. * Veeam Backup for AWS, the [Configuration Restore](https://helpcenter.veeam.com/docs/vbaws/guide/perform_config_restore.html?ver=10) section.  * Veeam Backup for Microsoft Azure, the [Configuration Restore](https://helpcenter.veeam.com/docs/vbazure/guide/configuration_restore.html?ver=8.1) section. |

Before you start the restore process, [check prerequisites](restore_vbr_before_you_begin.md). Then use the Veeam Backup & Replication Configuration Restore wizard to restore the configuration database.

1. [Launch the Veeam Backup & Replication Configuration Restore wizard](restore_vbr_launch.md).
2. [Select a restore mode](restore_vbr_mode.md).
3. [Select a configuration backup](restore_vbr_source.md).
4. [Review configuration backup parameters](restore_vbr_parameters.md).
5. [Specify password](vbr_restore_pass.md).
6. [Specify the target database](restore_vbr_target.md).
7. [Specify restore options](restore_vbr_options.md).
8. [Review restore settings](restore_vbr_review.md).
9. [Check configuration](restore_vbr_check_configuration.md).
10. [Finalize the restore process](restore_vbr_finalize.md).
11. [Synchronize backups and tape libraries](restore_vbr_rescan.md).
12. [Finish working with the wizard](vbr_config_summary.md).

Page updated 11/9/2025

Page content applies to build 13.0.1.1071
