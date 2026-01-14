---
title: "Veeam Backup Configuration Tool"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuration_tool.html"
last_updated: "8/2/2024"
product_version: "13.0.1.1071"
---

# Veeam Backup Configuration Tool

In this article

Veeam Backup & Replication comes with the Veeam.Backup.Configuration.Tool.exe utility that allows you to manage BCO files. BCO files are backup files that contain backups of configuration databases. Veeam Backup & Replication creates these files when it performs configuration backup. For more information on configuration backup, see [Managing Configuration Database](vbr_config.md).

You can use the Veeam Backup Configuration tool in the following scenarios:

* You do not have information on the BCO file version, parameters and attributes. In this case, you can use the tool to get details on the BCO file version.
* Veeam Backup & Replication is not able to restore a configuration database using a specific BCO file. In this case, you can use the tool to check if the BCO file is corrupted. The Veeam Backup Configuration tool will perform the cyclic redundancy check (CRC) and will verify that the encrypted file is decrypted properly.
* You do not have information on the specific configuration database. In this case, you can get details on its version and also use the tool to back up this database.
* Your backup server is no longer available, but your configuration database is still up and running. You can use the tool to create a backup of the configuration database and migrate this database to another backup server. In this case, the tool produces the same configuration backup, as Veeam Backup & Replication creates when you run the configuration backup job.

|  |
| --- |
| Note |
| If you back up the configuration database using the Veeam Backup Configuration tool, you will not be able to choose the backup repository in which the configuration backup must be stored and the necessary retention settings. Veeam Backup & Replication will keep last 10 restore points of the configuration backup in the default backup repository. If you want to change these setting, see the [Scheduling Configuration Backups](vbr_config_schedule.md) section. |

Page updated 8/2/2024

Page content applies to build 13.0.1.1071
