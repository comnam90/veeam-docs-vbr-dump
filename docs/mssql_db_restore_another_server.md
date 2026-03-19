---
title: "Restore to Another Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_db_restore_another_server.html"
last_updated: "3/13/2026"
product_version: "13.0.1.2067"
---

# Restore to Another Server


You can restore Microsoft SQL Server databases from Veeam Plug-In backups to another server. To restore databases to another server, you must specify an authentication method to access the backup created for the original server. Veeam Plug-In for Microsoft SQL Server supports the following authentication methods to access backups:

* Using credentials of the account under which the backup was created. For more information, see [Restore to Another Server Using Credentials](#creds).

This option is intended for backups created on the Microsoft SQL Server. To learn more, see [Performing Backup](mssql_protection.md).

* Using a recovery token. For more information, see [Restore to Another Server Using Recovery Token](#token).

This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication.To use this option, a backup administrator must create a recovery token for the backup in Veeam Backup & Replication. To learn more, see [Creating Recovery Token](application_backups_recovery_token.md).

Consider the following:

* For restore to another server, you can use either backups or backup copies of Microsoft SQL Server databases.
* If you perform restore from a backup that was imported to Veeam Backup & Replication, Veeam Plug-In will automatically create the backup job in Veeam Backup & Replication.
* During the restore process, backup operations are not disabled on the Microsoft SQL Server.

Restore to Another Server Using Credentials

To restore a database to another server, you can specify credentials of a user account under which the backup was created. To do this, do the following:

1. Go to %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ and run the following command:

|  |
| --- |
| MSSQLConfigTool.exe --set-auth-data-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using credentials of the account under which the backup was created, type 1:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

After that, you gain access to the backups according to the credentials that you specified.

1. Perform database restore using one of the following tools:

* The Restore Database wizard. For details, see [Restore with Restore Database Wizard](mssql_db_restore_ui.md).
* The MSSQLRecoveryManager.exe command-line tool. For details, see [Restore with Command-Line Interface](mssql_db_restore_cmd.md).

* Veeam Explorer for Microsoft SQL Server. For details, see [Restore with Veeam Explorer for Microsoft SQL Server](mssql_db_restore_vesql.md).

Keep in mind that the account must either have the Veeam Backup Administrator, or both the Veeam Backup Operator and Veeam Restore Operator roles. You can also use the account under which the backup was created. For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md)

Restore to Another Server Using Recovery Token

You can restore a database to another server using a recovery token generated in Veeam Backup & Replication and provided to you by a backup administrator. To do this, do the following:

1. Go to %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ and run the following command:

|  |
| --- |
| MSSQLConfigTool.exe --set-auth-data-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using a recovery token, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Credentials 2. Recovery token Enter authentication type number: 2 |

1. Veeam Plug-In will display the fingerprint of the Veeam Backup & Replication server and prompt you to provide a recovery token:

|  |
| --- |
| Veeam Backup & Replication server fingerprint: CA4F820F164C02A9AAC75562FC35330A93CDAA3C. Continue? (y/n) : y Enter recovery token: |

After that, you gain access to the backups for which the recovery token was generated.

1. Perform database restore using one of the following tools:

* The Restore Database wizard. For details, see [Restore with Restore Database Wizard](mssql_db_restore_ui.md).
* The MSSQLRecoveryManager.exe command-line tool. For details, see [Restore with Command-Line Interface](mssql_db_restore_cmd.md).

* Veeam Explorer for Microsoft SQL Server. For details, see [Restore with Veeam Explorer for Microsoft SQL Server](mssql_db_restore_vesql.md).


