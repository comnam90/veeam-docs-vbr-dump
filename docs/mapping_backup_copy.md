---
title: "Converting Backup Copy to Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mapping_backup_copy.html"
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
| If you want to restore from a backup copy, you don't need to convert the backup copy to backup. For details, see [Restore from Backup Copy](restore_from_copy.md). |

Procedure

To convert a backup copy to a primary backup, use the --promote-backup-copy-to-primary parameter as shown below:

1. Run the OracleRMANConfigTool with the --promote-backup-copy-to-primary parameter and type a backup copy number from the list of available backup copies.

|  |
| --- |
| OracleRMANConfigTool --promote-backup-copy-to-primary  Backup copies available for promotion to the primary backup target:  1. Backup Copy Job 1\ORCLSERV01 Oracle backup (Default Backup Repository)  Select a backup copy: 1  Changes to be applied to the RMAN configuration  CONFIGURE CHANNEL DEVICE TYPE SBT\_TAPE  PARMS 'SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VEEAMP~1\ORACLE~2.DLL'  FORMAT '94a7ac5a-2cb5-418b-8395-fb362d3aa182/RMAN\_%I\_%d\_%T\_%U.vab';  CONFIGURE CONTROLFILE AUTOBACKUP ON;  CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE SBT\_TAPE TO '%F\_RMAN\_AUTOBACKUP.vab';  CONFIGURE ARCHIVELOG BACKUP COPIES FOR DEVICE TYPE SBT\_TAPE TO 1;  CONFIGURE DATAFILE BACKUP COPIES FOR DEVICE TYPE SBT\_TAPE TO 1;    RMAN configuration to be applied:  SQL "alter system set backup\_tape\_io\_slaves=false deferred scope=both"; |

1. Converting a backup copy into regular backup file, requires changes in the RMAN configuration. You can allow the command to change RMAN configuration automatically, or you can change it manually. Select one of the options:

|  |
| --- |
| Proceed with the action?  1. Promote backup copy destination to the primary backup target and apply required configuration to RMAN automatically  2. Promote backup copy destination to the primary backup target and export required RMAN configuration (RMAN will have to be configured manually)  3. Cancel  Enter selection: 1  Promoting backup copy destination  Configuring RMAN  Done |


