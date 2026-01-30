---
title: "Restore to Another Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_restore_to_another.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Restore to Another Server


To restore a database to another server, you need to perform the following steps:

1. Create a database on the target server. The database must be empty, has the same name and volume sizes as the original database. To learn on how to create a database, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/44/eb166db6f0108ee10000000a11466f/frameset.htm).
2. Configure the environment on the target server to prepare a newly created database for the restore. The configured environment must match the original database environment. Otherwise, conflicts may arise. To learn more, see [Configuring Environment](plugins_sap_maxdb_deploy_configure.md).
3. Perform a full backup on the source server to generate files that are necessary for the restore. You must have at least one full backup on the source server.
4. Copy the following files from the original database folder to the database folder on the target server:

* backuphistory.adapter - the database backup history required by Veeam Backint
* dbm.ebf - Veeam backup tool integration data
* dbm.ebp - full protocol of the last Veeam backup
* dbm.knl - backup history recorded by the database kernel
* dbm.mdf - backup media history

The listed files may be located in different directories depending on the initial SAP MaxDB installation and database name.

For example:

|  |
| --- |
| /sapdb/MAXDB1/data/wrk/MAXDB1 |

1. Ensure that full permissions are granted to all files that you copied to the target server:

|  |
| --- |
| chmod 777 /<path> |

where <path> is the full path of the file.

For example:

|  |
| --- |
| chmod 777 /sapdb/MAXDB1/data/wrk/MAXDB1/backuphistory.adapter |

1. Using SapMaxDBBackintConfigTool, configure the backup for restore on the target server:

|  |
| --- |
| SapMaxDBBackintConfigTool --set-backup-for-restore |

Veeam Plug-In supports the following authentication methods to access backups:

* Using credentials of the account under which the backup was created. This option is intended for backups created using backup tools on the SAP MaxDB server. To learn more, see [Restore to Another Server Using Configured Authentication](#config).
* Using a security certificate. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. To learn more, see [Restore to Another Server Using Credentials](#creds).
* Using a recovery token. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. To use this option, a backup administrator must create a recovery token for the backup in Veeam Backup & Replication. To learn more, see [Restore to Another Server Using Recovery Token](#token).

1. Restore the database in the same manner as you restore a database to the original server. To learn more, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).

Restore to Another Server Using Configured Authentication

You can restore a database to another server using an account and authentication method that were specified in the Veeam Plug-In settings during the Veeam Plug-In configuration process. To do this, do the following:

1. Run the following command:

|  |
| --- |
| SapMaxDBBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using the authentication method that was specified during the Veeam Plug-In configuration process, type 1:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will display backups available for restore under the user account specified in the Veeam Plug-In configuration. The list of backups depends on the authentication method specified for the user account:

* For the user account with a security certificate, Veeam Plug-In displays backups created under this user account.
* For the user account with credentials, if the account has the Veeam Restore Operator role assigned in Veeam Backup & Replication, Veeam Plug-In displays all backups that reside in the backup repository. Otherwise, Veeam Plug-In displays backups created under the specified user account.
* For the user account with a recovery token, Veeam Plug-In displays backups for which the recovery token was generated.

|  |
| --- |
| Note |
| Keep in mind that Veeam Plug-In will list only those backups that were made on machines with the same architecture as the machine you are working on.  For example, if your machine has a x86\_64 architecture, only backups made on machines with the x86\_64 architecture will be displayed. |

Select a backup to start the restore process:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Restore the database in the same manner as you restore a database to the original server. To learn more, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).

Restore to Another Server Using Credentials

To restore a database to another server, you can specify credentials of a user account under which the backup was created. To do this, do the following:

1. Run the following command:

|  |
| --- |
| SapMaxDBBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using credentials of the account under which the backup was created, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Currently set authentication data 2. Credentials 3. Recovery token Enter authentication type number: 2 |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

1. Veeam Plug-In will display backups available for restore under the specified user account. If the account has the Veeam Restore Operator role assigned in Veeam Backup & Replication, Veeam Plug-In displays all backups that reside in the backup repository. Otherwise, Veeam Plug-In displays backups created under the specified user account.

Select a backup to start the restore process:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Restore the database in the same manner as you restore a database to the original server. To learn more, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).

Restore to Another Server Using Recovery Token

You can restore a database to another server using a recovery token generated in Veeam Backup & Replication and provided to you by a backup administrator or by a restore operator. To do this, do the following:

1. Run the following command:

|  |
| --- |
| SapBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using a recovery token, type 3:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Currently set authentication data 2. Credentials 3. Recovery token Enter authentication type number: 3 |

1. Veeam Plug-In will display the fingerprint of the Veeam Backup & Replication server and prompt you to provide a recovery token:

|  |
| --- |
| Veeam Backup & Replication server fingerprint: CA4F820F164C02A9AAC75562FC35330A93CDAA3C. Continue? (y/n) : y Enter recovery token: |

1. Veeam Plug-In will display backups for which the recovery token was generated. Select the necessary backup:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Restore the database in the same manner as you restore a database to the original server. To learn more, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).


