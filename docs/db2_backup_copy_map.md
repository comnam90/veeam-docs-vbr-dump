---
title: "Converting Backup Copy to Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_backup_copy_map.html"
last_updated: "3/7/2025"
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
| If you want to restore from a backup copy, you do not need to convert the backup copy to the backup. For details, see [Restore from Backup Copy](restore_from_copy.md). |

Procedure

To convert a backup copy to a primary backup, use the --promote-backup-copy-to-primary parameter as shown below:

1. Run the DB2ConfigTool with the --promote-backup-copy-to-primary parameter and type a backup copy number from the list of available backup copies.

|  |
| --- |
| DB2ConfigTool --promote-backup-copy-to-primary  Backup copies available for promotion to the primary backup target:  1. DB2 Backup Copy Job 1\db2ubuntu IBM Db2 backup (Scale-out Backup Repository 1)  Select a backup copy: 1 |

1. Converting a backup copy into regular backup file, requires changes in the Veeam Plug-In configuration. Select option 1 to continue:

|  |
| --- |
| Proceed with the action?  1. Promote backup copy destination to the primary backup target and apply the required configuration automatically  2. Cancel  Enter selection: 1  Promoting backup copy destination  Done |


