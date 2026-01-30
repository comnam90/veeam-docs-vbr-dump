---
title: "Converting Backup Copy to Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mapping_backup_copy_mssql.html"
last_updated: "11/7/2025"
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
| If you want to restore from a backup copy, you do not need to convert the backup copy to the backup. |

Procedure

To convert a backup copy to a primary backup, do the following:

1. Run the MSSQLConfigTool.exe command-line tool with the --promote-backup-copy-to-primary parameter:

|  |
| --- |
| MSSQLConfigTool.exe --promote-backup-copy-to-primary |

1. Veeam Plug-In will display the list of available backup copies. Type the necessary backup copy number and press [Enter]. Then follow instructions in the command prompt.

|  |
| --- |
| Backup copies available for promotion to the primary backup target:  1. Backup Copy Job 1\SERV01 Microsoft SQL backup (Default Backup Repository)  Select a backup copy: 1  Proceed with the action?  1. Promote backup copy destination to the primary backup target  2. Cancel  Enter selection: 1  Promoting backup copy destination  Done |


