---
title: "Managing Configuration Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config.html"
last_updated: "11/24/2025"
product_version: "13.0.1.1071"
---

# Managing Configuration Database


You can back up and restore the configuration database that Veeam Backup & Replication uses. If the backup server fails for some reason, you can re-install the backup server and quickly restore its configuration from the configuration backup. You can also use configuration backups to apply the configuration of one backup server to another backup server in the backup infrastructure. During configuration backup, Veeam Backup & Replication exports data from the configuration database and saves it to a backup file in the backup repository.

|  |
| --- |
| Note |
| If you use cloud plug-ins to protect VMs in AWS, Microsoft Azure and other environments, you can also back up configurations of cloud backup appliances. To back up the configurations, you must enable encryption as described in section [Creating Encrypted Configuration Backups](config_backup_encrypted.md).  For more information on appliance configuration backup and restore, see the following guides:   * Veeam Backup for Google Cloud, the [Performing Configuration Backup and Restore](https://helpcenter.veeam.com/docs/vbgc/guide/performing_configuration_backup_restore.html?ver=7) section. * Veeam Backup for AWS, the [Performing Configuration Backup and Restore](https://helpcenter.veeam.com/docs/vbaws/guide/config_backup.html?ver=10) section. * Veeam Backup for Microsoft Azure, the [Performing Configuration Backup and Restore](https://helpcenter.veeam.com/docs/vbazure/guide/configuration_backup_and_restore.html?ver=8.1) section. |

It is recommended that you regularly perform configuration backup for every backup server in the backup infrastructure. Periodic configuration backups reduce the risk of data loss and minimize the administrative overhead if any problem with backup servers occurs.

|  |
| --- |
| Note |
| If you have a hardened repository in your backup infrastructure, you must enable data encryption for configuration backup. Otherwise, you cannot perform configuration backups. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md). |

Do not back up the backup server configuration using backup or replication jobs in Veeam Backup & Replication. For backup and replication, Veeam Backup & Replication uses VM snapshots. During snapshot creation and commit, the VM freezes for some time, which can potentially lead to the following consequences:

* Disconnection from the configuration database. For more information, see [this Veeam KB article](https://www.veeam.com/kb1681).
* Disconnection from remote Veeam Backup & Replication agents.
* Disconnection from network storage (for example, storage presented through iSCSI) and so on.

For this reason, you must always use the configuration backup functionality to back up and restore configuration of the backup server.

Related Topics

* [Creating Configuration Backups](export_vbr_config.md)
* [Restoring Configuration Database on Windows-Based Backup Server](vbr_config_restore.md)
* [Migrating Veeam Backup & Replication to Another Windows-Based Backup Server](vbr_config_migrate.md)
* [Migrating Veeam Backup & Replication to Linux-Based Backup Server](vbr_config_win_to_lin_migrate.md)
* [Migrating Configuration Database to Another SQL Server](vbr_config_migrate_to_another_server.md)
* [Migrating Configuration Database to PostgreSQL Server](vbr_config_migrate_to_postgresql.md)
* [Automating Configuration Database Restore](vbr_config_restore_automated.md)
* [Restoring Configuration Database on Linux-Based Backup Server](vbr_config_restore_linux.md)


