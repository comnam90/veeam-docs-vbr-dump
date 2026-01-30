---
title: "Converting Backup Copy to Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mapping_backup_copy_hana.html"
last_updated: "10/25/2024"
product_version: "13.0.1.1071"
---

# Converting Backup Copy to Backup


If you have imported Veeam Plug-In backup copies from another server, you can convert them into regular backup files. When you convert a backup copy to a backup, Veeam Plug-In creates a backup job with the converted backup. You can use this backup job to continue a backup chain and use the converted backup as a restore point.

You can convert and unbind Veeam Plug-In backups into regular Veeam Plug-In backup files in the following cases:

* If you have deleted a backup copy job which created the backup copy.
* If you have excluded a backup job from a backup copy job that used multiple backup jobs as a source.
* If you imported a Veeam Plug-In backup copy from another host.

|  |
| --- |
| Note |
| If you want to restore from a backup copy, you don't need to convert the backup copy to backup. For details, see [Restore from Backup Copy](restore_from_copy_saphana.md). |

Converting Backup Copy to Backup for SAP HANA

To convert a backup copy to a primary backup, use the --promote-backup-copy-to-primary parameter as shown below:

|  |
| --- |
| SapBackintConfigTool --promote-backup-copy-to-primary  Backup copies available for promotion to primary backup:  1. Backup Copy Job 1\saprhel01-localdomain SAP backint backup (Default Backup Repository)  Select backup: 1  Promotion of backup copy to a primary backup will reconfigure the plug-in to use a different repository. Continue? (y/N): y |

|  |
| --- |
| Important |
| [For backups of scale-out clusters and servers with the customServerName option] To avoid failure of conversion of backup copies, the cluster name must be the same as the name used in the backup copy. |


