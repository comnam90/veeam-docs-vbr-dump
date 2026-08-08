---
title: "Performing Configuration Backup Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_backup_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Configuration Backup Using Console


When Veeam Backup & Replication performs configuration backup, it backs up the configuration of the backup server and also configurations of all backup appliances added to the backup infrastructure. The results of every configuration backup session are displayed in the History view under the System node.

You can perform configuration backup manually or instruct Veeam Backup & Replication to do it automatically on a regular basis:

* To perform configuration backup manually, follow the instructions provided in [Running Configuration Backups Manually](vbr_config_manually.md).

* To instruct Veeam Backup & Replication to perform configuration backup automatically, follow the instructions provided in [Scheduling Configuration Backups](vbr_config_schedule.md).

|  |
| --- |
| Important |
| For Veeam Backup & Replication to be able to back up configurations of managed backup appliances, you must enable backup file encryption in the configuration backup settings. |

Before You Begin

If you plan to back up the configuration of a managed backup appliance, keep in mind the following limitations and considerations:

* You must enable backup file encryption in the configuration backup settings. Otherwise, Veeam Backup & Replication will not be able to back up the backup appliance configuration.

To learn how to enable backup file encryption, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).

* You must log in to the Host Management Console using the credentials of a user account with the Security Officer role and specify a passphrase for this account. Otherwise, Veeam Backup & Replication will not be able to back up the backup appliance configuration.

To learn how to specify passphrases for user accounts with the Security Officer role, see [Performing Initial Security Officer Login](hmc_users_security_officer.md).

* You cannot store configuration backups in scale-out backup repositories and external repositories.

* For Veeam Backup & Replication to be able to back up the appliance configuration, the backup appliance must be available and must run a backup appliance version that is compatible with the Veeam Backup & Replication version.

For the list of compatible versions, see [System Requirements](azure_system_requirements.md#compatibility).

* During configuration backup, Veeam Backup & Replication can process only 3 appliances at once — the appliances exceeding this limit are queued.
* To enable data loss protection in case you lose or forget the password used for data encryption, you can use Veeam Backup Enterprise Manager to decrypt backup files.

To learn how to let Veeam Backup & Replication encrypt and decrypt data with Enterprise Manager, see the Veeam Backup Enterprise Manager Guide, section [Managing Encryption Keys](https://helpcenter.veeam.com/docs/backup/em/em_manage_keys.html?ver=120).

Configuration Backup Location

Veeam Backup & Replication stores configuration backups of backup appliances in a repository specified in the configuration backup settings. Backups are saved to the \\VeeamConfigBackup\Azure folder.

|  |
| --- |
| Note |
| Consider the following:   * It is not recommended that you store configuration backups on the backup server. Otherwise, you will not be able to restore the configurations of managed backup appliances in case the backup server goes down. * If the name of an appliance contains unsupported characters, these characters are replaced with the '\_' underscore symbol in the name format for a subfolder and a backup file. |

Page updated 2026-07-01

