---
title: "Converting Backup Copy to Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mapping_backup_copy_sap_orcl.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Converting Backup Copy to Backup


If you have imported backup copy files created by a [backup copy job](backup_copy_main_sap_oracle.md) from another repository, you can convert them into regular backup files. When you convert backup copy files to regular backup files, Veeam Plug-In creates a backup job and attaches the converted backup files to it. You can use this backup job to continue the backup chain and use converted backup files as a restore point.

You can convert imported Veeam Plug-In backups into regular Veeam Plug-In backup files in the following cases:

* If you have deleted a backup copy job which created the backup copy.
* If you have excluded a backup job from a backup copy job that used multiple backup jobs as a source.
* If you have imported a Veeam Plug-In backup copy from another repository.

|  |
| --- |
| Note |
| If you want to restore from a backup copy, you don't need to convert the backup copy to backup. For details, see [Restore from Backup Copy](restore_from_copy_sap_orcl.md). |

Converting Backup Copy to Backup for SAP HANA

To convert a backup copy to a primary backup, use the --promote-backup-copy-to-primary parameter as shown below:

|  |
| --- |
| SapOracleBackintConfigTool --promote-backup-copy-to-primary  Backup copies available for promotion to primary backup:  1. Backup Copy Job 1\saprhel01-localdomain SAP backint backup (Default Backup Repository)  Select backup: 1  Promotion of backup copy to a primary backup will reconfigure the plug-in to use a different repository. Continue? (y/N): y |

|  |
| --- |
| Important |
| [For servers with the customServerName option] To avoid failure of conversion of backup copies, the server name must be the same as the name used in the backup copy. |


