---
title: "Creating Configuration Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/export_vbr_config.html"
last_updated: "11/9/2025"
product_version: "13.0.1.1071"
---

# Creating Configuration Backups

In this article

By default, Veeam Backup & Replication creates a configuration backup daily. You can change the schedule or create a configuration backup manually. You can choose the backup repository in which the configuration backup must be stored, specify the necessary retention settings. Veeam Backup & Replication allows you to create immutable configuration backups.

For more information on managing configuration backup, see the following topics:

* [Scheduling Configuration Backups](vbr_config_schedule.md)
* [Configuring Notification Settings for Configuration Backups](vbr_config_notifications.md)
* [Running Configuration Backups Manually](vbr_config_manually.md)
* [Creating Encrypted Configuration Backups](config_backup_encrypted.md)
* [Creating Immutable Configuration Backups](config_backup_immutable.md)

Configuration Backup Files

When you perform configuration backup, Veeam Backup & Replication retrieves data for the backup server from the configuration database, writes this data into a set of XML files and archives these XML files to a backup file of the BCO format.

Veeam Backup & Replication exports information about the following objects:

* Backup infrastructure components and objects: hosts, servers, backup proxies, repositories, WAN accelerators, virtual lab configurations, global settings configured on the backup server and so on.
* Backups: backups and backup copies, replicas, CDP policies created on the backup server.
* Sessions: job sessions performed on the backup server.
* Tapes: tape libraries connected to the backup server.

|  |
| --- |
| Note |
| Consider the following:   * If a configuration backup job has a remote repository as a target, a temporary BCO file is created in the %TEMP% folder during the job (by default, this is C:\Windows\Temp, but it can be modified in the environment variables). After the BCO file is copied to the remote repository, it is removed from %TEMP%. If the repository is local, the BCO file is saved directly to it without using %TEMP%.   Therefore, there must be enough free space on the disk for this temporary BCO file if the remote repository is used for storing the configuration backup. The size of the BCO file depends on the size of the database and its content (for example, sessions are compressed better than tapes in BCO). The compression ratio can be checked in the configuration backup session details.   * If you use custom configuration registry values, note that configuration backup will not apply to them. You may want to back them up manually. * The configuration backup job creates a snapshot of the configuration database and retrieves data required for successful restore from it. If the database size is large, the job may produce significant load on the Microsoft SQL Server. Make sure that you schedule the configuration backup job for a period of low operation intensity on the backup server. |

Backup Repository Target

The resulting configuration backup file is stored in the \VeeamConfigBackup\%BackupServer% folder on the default backup repository. However, for security sake, it is recommended that you do not store configuration backups on the default backup repository or in any other folder on the backup server. In this case, if the backup server fails, its configuration data will remain, and you will be able to recover the failed backup server. You can store configuration backups on repositories of different types, including Veeam Cloud Connect repositories.

|  |
| --- |
| Important |
| You cannot store configuration backups in [external repositories](external_repository.md) and [scale-out backup repositories](backup_repository_sobr.md). |

When you configure a new backup repository, Veeam Backup & Replication offers you to change the configuration backup file location from the default backup repository to the new backup repository. Click Yes, and Veeam Backup & Replication will automatically change the backup target in the configuration backup job settings and will use this target in future.

Configuration backups that were created before the target change will remain in the default backup repository. You can manually copy them to the new backup repository to have all restore points of the configuration backup in one place.

Page updated 11/9/2025

Page content applies to build 13.0.1.1071
