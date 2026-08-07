---
title: "Performing Configuration Backup Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_config_backup_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Configuration Backup Using Console


While performing configuration backup, Veeam Backup & Replication backs up the configuration of the backup server and also configurations of all backup appliances added to the backup infrastructure. The results of every configuration backup session are displayed in the History view under the System node.

You can perform configuration backup manually or instruct Veeam Backup & Replication to do it automatically on a regular basis:

* To perform configuration backup manually, follow the instructions provided in section [Running Configuration Backups Manually](vbr_config_manually.md).
* To instruct Veeam Backup & Replication to perform configuration backup automatically, follow the instructions provided in section [Scheduling Configuration Backups](vbr_config_schedule.md).

Before You Begin

If you plan to back up the configuration of a managed backup appliance, keep in mind the following limitations and considerations:

* You must enable backup file encryption in the configuration backup settings. Otherwise, Veeam Backup & Replication will not be able to back up the backup appliance configuration.

To learn how to create encrypted configuration backup, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).

* You must log in to the Host Management Console using the credentials of a user account with the Security Officer role and specify a passphrase for this account. Otherwise, Veeam Backup & Replication will not be able to back up the backup appliance configuration.

To learn how to specify passphrases for user accounts with the Security Officer role, see [Performing Initial Security Login](hmc_users_security_officer.md).

* You cannot store configuration backups in scale-out backup repositories and external repositories.
* For Veeam Backup & Replication to be able to back up the appliance configuration, the backup appliance must be available and must run a backup appliance version that is compatible with the Veeam Plug-in for AWS version.

For the list of compatible versions, see [System Requirements](aws_system_requirements.md#versions).

* During configuration backup, Veeam Backup & Replication processes only 3 appliances at a time — the appliances exceeding this limit are queued.

* To enable data loss protection in case you lose or forget the password used for data encryption, you can use Veeam Backup Enterprise Manager to decrypt backup files.

To learn how to let Veeam Backup & Replication encrypt and decrypt data with Enterprise Manager, see the Veeam Backup Enterprise Manager Guide, section [Managing Encryption Keys](https://helpcenter.veeam.com/docs/backup/em/em_manage_keys.html?ver=120).

Configuration Backup Location

Veeam Backup & Replication stores configuration backups of backup appliances in a repository specified in configuration backup settings. Backups are saved in the \VeeamConfigBackup\AWS folder.

|  |
| --- |
| Notes |
| * It is not recommended to store configuration backups on the backup server. Otherwise, you will not be able to restore configuration of managed backup appliances in case the backup server goes down.  * If the name of an appliance contains unsupported characters, these characters are replaced with the '\_' underscore symbol in the names of subfolders and backup files. |

Page updated 2026-06-02

