---
title: "Restore to Another Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_other_server_rman.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Restore to Another Server


If you want to restore Oracle databases from a Veeam Plug-In backup to another server, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/21/bradv/rman-recovery-advanced.html#GUID-6B71E7DF-A2B6-44F5-A8D5-B184BB41A768) and consider the specifics described in this section.

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In must be installed and configured on the target server. * You can restore a database to the target server only if it runs the same OS as the original server. For example, you cannot restore a database from the Windows-based system to the Linux-based system.   This limitation also applies to Linux distributions. The target server must run the same distribution as the original server. For example, you cannot restore a database from the server running Oracle Linux to the target server running CentOS. |

To restore an Oracle database to another server, use the following commands:

1. ALLOCATE CHANNEL. Use this command to manually allocate a channel or channels between RMAN and the database instance. Specify the following parameters:

1. Assign an ID for the channel. For example: ch1.
2. Specify the SBT\_TAPE option for the DEVICE TYPE or TYPE parameter.
3. Specify PARMS to define other parameters for the sbt\_tape channel.
4. Specify which media library must be used for this sbt\_tape channel. For Linux or Unix, set the path to the libOracleRMANPlugin.so file as the SBT\_LIBRARY. For Microsoft Windows, set the path to %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANPlugin.dll.

1. SEND. Use this command with the srcBackup=BackupID parameter to specify the ID of the backup from which you want to restore a database. For example: "srcBackup=6109d377-93b5-4741-a796-03471d2795cd".

To obtain a backup ID, do the following:

1. Specify an authentication method to access the backup created for the original server. For details, see [Specifying Authentication Settings](#auth).
2. Select the backup from which you want to restore a database. For details, see [Selecting Backup](#backup).

|  |
| --- |
| Important |
| The ALLOCATE CHANNEL and SEND commands must be issued only within a RUN block for a specific restore operation. |

The following examples show scripts for restoring the control file and restoring the Oracle database to another server using the SEND command in different OSes:

* For Linux and Unix machines:

|  |
| --- |
| RUN {       ALLOCATE CHANNEL ch1 TYPE sbt\_tape PARMS "SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so";      SEND "srcBackup=6109d377-93b5-4741-a796-03471d2795cd";      SET CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE 'SBT\_TAPE' TO '%F\_RMAN\_AUTOBACKUP.vab';      RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; |

* For Microsoft Windows machines:

|  |
| --- |
| RUN {       ALLOCATE CHANNEL ch1 TYPE sbt\_tape PARMS "SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANPlugin.dll";      SEND "srcBackup=6109d377-93b5-4741-a796-03471d2795cd";      SET CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE 'SBT\_TAPE' TO '%F\_RMAN\_AUTOBACKUP.vab';      RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; |

Consider the following:

* If you do not use the SEND command, Veeam Plug-In will restore data from a backup created for the server on which Veeam Plug-In is currently running instead of restoring data from a backup created on another server.
* For restore to another server, you can use either backups or backup copies of Oracle databases.
* If you perform restore from a backup that was imported to Veeam Backup & Replication, Veeam Plug-In will automatically create the backup job in Veeam Backup & Replication.
* During the restore process, backup operations are not disabled on the Oracle server.

Specifying Authentication Settings

To restore databases to another server, you must specify an authentication method to access the backup created for the original server. Veeam Plug-In for Oracle RMAN supports the following authentication methods to access backups:

* Using credentials of the account under which the backup was created. For more information, see [Specifying Credentials](#creds).

This option is intended for backups created using Oracle RMAN commands on the Oracle server.

* Using a recovery token. For more information, see [Specifying Recovery Token](#token).

This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. To use this option, a backup administrator must create a recovery token for the backup in Veeam Backup & Replication.

Specifying Credentials

To restore a database to another server, you can specify credentials of a user account under which the backup was created. To do this, do the following:

1. Access the Veeam Plug-In for Oracle RMAN directory on your machine. The path to the directory differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN
* On machines running Microsoft Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN

1. Run the following command:

|  |
| --- |
| OracleRMANConfigTool --set-auth-data-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup.

If you want to access the backup using account credentials, the account must meet the following requirements:

* The account must either have the Veeam Backup Administrator, or both the Veeam Backup Operator and Veeam Restore Operator roles. You can also use the account under which the backup was created. For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).
* The account must have access permissions to the backup repository where the backup is stored. For more information, see [Access and Encryption Settings on Repositories](repository_permissions_rman.md).

To access the backup using account credentials, type 1:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

Specifying Recovery Token

You can restore a database to another server using a recovery token generated in Veeam Backup & Replication and provided to you by a backup administrator. To do this, do the following:

1. Access the Veeam Plug-In for Oracle RMAN directory on your machine. The path to the directory differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN
* On machines running Microsoft Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN

1. Run the following command:

|  |
| --- |
| OracleRMANConfigTool --set-auth-data-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using a recovery token, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Credentials 2. Recovery token Enter authentication type number: 2 |

1. Veeam Plug-In will display the fingerprint of the Veeam Backup & Replication server and prompt you to provide a recovery token:

|  |
| --- |
| Veeam Backup & Replication server fingerprint: CA4F820F164C02A9AAC75562FC35330A93CDAA3C. Continue? (y/n) : y Enter recovery token: The specified authentication data will be used automatically to access backups over the SEND command |

Selecting Backup

After you specify authentication settings to access the backup from which you want to restore a database on another server, you can select the backup. To do this, do the following:

1. Access the Veeam Plug-In for Oracle RMAN directory on your machine. The path to the directory differs depending on the OS of the machine where Veeam Plug-In is installed:

* On machines running Linux or Unix OS: /opt/veeam/VeeamPluginforOracleRMAN
* On machines running Microsoft Windows OS: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN

1. Run the following command:

|  |
| --- |
| OracleRMANConfigTool --get-backup-for-restore |

1. Veeam Plug-In will display backups available for restore. The list of backups depends on the authentication settings that you specified:

* If you specified credentials of a user account that has the Veeam Backup Administrator or Veeam Restore Operator role assigned in Veeam Backup & Replication, Veeam Plug-In displays all backups that reside in the backup repository. Otherwise, Veeam Plug-In displays backups created under the specified user account.
* If you specified a recovery token, Veeam Plug-In displays backups for which the recovery token was generated.

Select the backup to obtain the backup ID:

|  |
| --- |
| Select backup to be used: 1. Backup1 Oracle backup (Default Backup Repository) 2. Backup2 Oracle backup (Default Backup Repository) 3. Backup3 Oracle backup (Default Backup Repository) Enter backup number: 3 To perform restore operations, use ID of the selected backup from the example below as srcBackup parameter value in SEND command: ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so'; SEND 'srcBackup=6109d377-93b5-4741-a796-03471d2795cd'; |


