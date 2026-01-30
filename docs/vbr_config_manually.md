---
title: "Running Configuration Backups Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_manually.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Running Configuration Backups Manually


You can create a configuration backup manually when you need it, for example, if you want to capture a state of the configuration database at a specific point in time.

|  |
| --- |
| Important |
| If you plan to migrate configuration data to the database used by another backup server, stop all running jobs and disable scheduled jobs before creating the configuration backup. In the opposite case, job sessions may be failing after configuration restore. For more information, see [Migrating Veeam Backup & Replication to Another Backup Server](vbr_config_migrate.md). |

To create a configuration backup manually:

1. From the main menu, select Configuration Backup.
2. Make sure that the Enable configuration backup to the following repository check box is selected.
3. From the Backup repository list, choose a backup repository on which the configuration backup must be stored.
4. In the Restore points to keep field, specify the number of restore points that you want to maintain in the backup repository.
5. To create an encrypted backup, select the Enable backup file encryption check box. From the Password field, select a password you want to use for encryption. If you have not created a password beforehand, click Add or use the Manage passwords link to specify a new password. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).
6. Click Backup now.

Veeam Backup & Replication will back up the configuration database and store a new restore point to the selected backup repository. The resulting configuration backup file (.BCO) is stored in the \VeeamConfigBackup\%BackupServer% folder on the repository you have selected. The file name contains the date when the configuration backup was performed.

![Running Configuration Backups Manually](images/schedule_config_backup.webp)


