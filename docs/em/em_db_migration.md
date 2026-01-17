---
title: "Migrating Enterprise Manager from Microsoft SQL Server to PostrgeSQL"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_db_migration.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---


In this article

You can migrate the Enterprise Manager configuration database from Microsoft SQL Server to PostgreSQL. To perform the migration, back up the Enterprise Manager configuration database based on Microsoft SQL Server and restore it to PostgreSQL.

Enterprise Manager migration lets you change the engine of the Enterprise Manager configuration database and keep existing Enterprise Manager configurations including notification settings, Enterprise Manager accounts and roles, retention settings for index files and event history, self-service configurations for the Veeam Self-Service Backup Portal and vSphere Self-Service Backup Portal, SAML authentication settings, directory account settings, key management settings and encryption keys.

Before You Begin

Before you migrate the Enterprise Manager configuration database from Microsoft SQL Server to PostgreSQL, consider the following:

* Source Microsoft SQL Server and target PostgreSQL must be set up and running.
* To migrate the configuration database from Microsoft SQL Server to PostgreSQL and attach it to a newer version of Enterprise Manager, first upgrade Enterprise Manager to the newer version to ensure the database structure matches the new version, and then migrate the database from Microsoft SQL Server to PostgreSQL.
* Data that Enterprise Manager collects from backup servers (such as backup jobs, session logs, backed-up objects and so on) is not migrated. This data will be collected again after the first data collection run after migration. For details, see [Collecting Data from Backup Servers](collecting_data_from_backup_servers.md).

Account Permissions

The Enterprise Manager Database Migration utility requires access to the registry so you must run the command-line shell as administrator. In addition, make sure that the accounts used to run the utility and connect to the target PostgreSQL database have the necessary permissions.

| Command | Required Permissions |
| --- | --- |
| /backupemdatabase | The account that runs the /backupemdatabase command must either be the Enterprise Manager service account or any other account with the following permissions:   * Local Administrator permissions on the Enterprise Manager server. * Log on as a service permission. * The account must also be assigned either of the following roles on the level of the Microsoft SQL Server database:  * db\_owner role * db\_datareader and db\_datawriter roles |
| /restoreemdatabase | The account that you specify to authenticate against a PostgreSQL server in the /login parameter must be a superuser. If you don't specify any parameter, the utility will use the account under which the Veeam Backup Enterprise Manager Service is running. |

Performing Migration

To migrate Enterprise Manager, you can use the Enterprise Manager Database Migration utility. The utility supports both local (when the database is located on the same machine with Enterprise Manager) and remote Microsoft SQL Server databases (when the database is located on another machine).

The Enterprise Manager Database Migration utility comes with Veeam Backup Enterprise Manager and is located on the Enterprise Manager server in the installation folder. The default path is the following: %PROGRAMFILES%\Veeam\Backup and Replication\Enterprise Manager\Veeam.EM.DB.Migration.exe. To run the utility, use a command-line shell.

To migrating Enterprise Manager from Microsoft SQL Server to PostgreSQL, follow these steps:

1. Back up the Enterprise Manager configuration database to an EMCO backup file.

|  |
| --- |
| Veeam.EM.DB.Migration.exe /file:"C:\EM Configuration\02.emco" /backupemdatabase /encryptionpassword:Password01 /encryptionhint:thatpass |

where:

* /file:"C:\EM Configuration\02.emco" — file name and location of the backup file. If you specify a folder that does not exist, the utility will create it. If a file with the specified name already exists, it will be rewritten.
* /backupemdatabase — utility backup mode.
* /encryptionpassword:Password01 — encryption password for the backup file.
* /encryptionhint:thatpass — password hint.

Microsoft SQL Server connection settings are not required in the command, the utility gets them from the registry.

1. Restore the Enterprise Manager configuration database from an EMCO backup file to PostgreSQL.

|  |
| --- |
| Veeam.EM.DB.Migration.exe /file:"C:\EM Configuration\02.emco" /restoreemdatabase /encryptionpassword:Password01 /servername:enterprise05 /initialcatalog:VeeamBackupReporting\_01 /serverport:5434 /login:postgres /password:Password02 |

where:

* /file:"C:\EM Configuration\02.emco" — file name and location of the backup file.
* /restoreemdatabase — utility restore mode.
* /encryptionpassword:Password01 — encryption password for the backup file.
* /servername:enterprise05 — name of the target PostgreSQL server.
* /initialcatalog:VeeamBackupReporting\_01 — target PostgreSQL instance.
* /serverport:5434 — port number of the target PostgreSQL instance.
* /login:postgres — account name used to authenticate against the PostgreSQL server.
* /password:Password02 — password used to authenticate against the PostgreSQL server.

1. Connect Enterprise Manager to the restored database using the Configuration Database Connection Settings utility. For more information, see [Connecting Enterprise Manager to Another Configuration Database](dbconfig_utility.md).

Utility Syntax

With the Enterprise Manager Database Migration utility, you can perform the following operations:

* Back up a Microsoft SQL Server database to an EMCO backup file:

|  |
| --- |
| Veeam.EM.DB.Migration.exe /file:value /backupemdatabase [/encryptionpassword:value] [/encryptionhint:value] [/verbose] |

* Restore a Microsoft SQL Server database from a backup file to PostgreSQL:

|  |
| --- |
| Veeam.EM.DB.Migration.exe /file:<value> /restoreemdatabase [/encryptionpassword:<value>] [/servername:<value>] [/serverport:<value>] [/initialcatalog:<value>] [/login:<value>] [/password:<value>] [/verbose] |

* Display the utility help:

|  |
| --- |
| Veeam.EM.DB.Migration.exe /? |

Utility Parameters

The table below describes parameters that you can use to back up and restore the Enterprise Manager configuration database.

| Parameter | Description |
| --- | --- |
| /? | Displays help. |
| /file:<value> | Specifies file name and location of an EMCO backup file. |
| /encryptionpassword:<value> | Specifies a password for backup file encryption. |
| /encryptionhint:<value> | Specifies a hint for the encryption password. |
| /backupemdatabase | Backs up the Enterprise Manager configuration database based on Microsoft SQL Server to an EMCO backup file. Note the command cannot back up a PostgreSQL database. |
| /restoreemdatabase | Restores the Enterprise Manager configuration database from an EMCO backup file to PostgreSQL. |
| /servername:<value> | Specifies a name or IP address of the target host with PostgreSQL server. The default value is localhost. If you skip the parameter, the default value is used. |
| /serverport:<value> | Specifies a port number of a PostgreSQL instance. The default value is 5432. If you skip the parameter, the default value is used. |
| /initialcatalog:<value> | Specifies a name of a target PostgreSQL database. The default value is VeeamBackupReporting. If you skip the parameter, the default value is used.  If a database with the specified name (or the default name) exists, the utility adds an increment postfix to the database name, for example: VeeamBackupReporting\_00, VeeamBackupReporting\_01. |
| /login:<value> | Specifies an account name that the utility uses to authenticate against a PostgreSQL server. By default, the utility uses the account under which the Veeam Backup Enterprise Manager Service is running. The chosen PostgreSQL account must be a superuser. |
| /password:<value> | Specifies a password that the utility uses to authenticate against a PostgreSQL server. By default, the utility uses the account under which the Veeam Backup Enterprise Manager Service is running. |
| /verbose | Enables verbose logging mode. Logs are stored in the following directory: %PROGRAMDATA%\Veeam\Backup\Utils\Util.EmTransfer. |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
