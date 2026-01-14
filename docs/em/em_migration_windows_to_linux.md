---
title: "em_migration_windows_to_linux"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_migration_windows_to_linux.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---


In this article

You can migrate Enterprise Manager from a Microsoft Windows-based machine to a Linux-based machine. To perform the migration, back up the Enterprise Manager configuration database and restore it to the Linux machine where Enterprise Manager is already deployed.

Enterprise Manager migration preserves existing Enterprise Manager configurations including notification settings, Enterprise Manager accounts and roles, retention settings for index files and event history, self-service configurations for the Veeam Self-Service Backup Portal and vSphere Self-Service Backup Portal, SAML authentication settings, directory account settings, key management settings and encryption keys.

Before You Begin

Before you migrate the Enterprise Manager configuration database from a Microsoft Windows-based machine to a Linux-based, consider the following:

* Enterprise Manager of the same build must be installed on both the Microsoft Windows and Linux machines. For deployment instructions, see [Enterprise Manager Deployment on Linux](em_deployment_linux.md) and [Enterprise Manager Deployment on Windows](em_deployment_windows.md).
* The Microsoft Windows installation of Enterprise Manager must use PostgreSQL as its configuration database. If the database is based on Microsoft SQL Server, first migrate it to PostgreSQL. For details, see [Migrating Enterprise Manager from Microsoft SQL Server to PostrgeSQL](em_db_migration.md).

* PostgreSQL must be set up and running on the source and target machines.

* Data that Enterprise Manager collects from backup servers (such as backup jobs, session logs, backed-up objects and so on) is not migrated. This data will be collected again after the first data collection run after migration. For details, see [Collecting Data from Backup Servers](collecting_data_from_backup_servers.md).

* After you successfully migrate Enterprise Manager to Linux, local Microsoft Windows users will not be migrated (local Microsoft Windows groups may appear but cannot be used on Linux). Domain Active Directory users and groups will be preserved if Veeam Software Appliance is joined to the same Active Directory domain. The veeamadmin account will be automatically assigned the Enterprise Manager Administrator role.

Performing Migration

To migrate Enterprise Manager from Microsoft Windows to Linux, you can use the Enterprise Manager Database Migration utility. The utility supports both local (when the database is located on the same machine with Enterprise Manager) and remote PostgreSQL databases (when the database is located on another machine).

The Enterprise Manager Database Migration utility comes with Veeam Backup Enterprise Manager and is located on the Enterprise Manager server in the installation folder. The default path is the following:

* On Microsoft Windows-based machine:

|  |
| --- |
| %PROGRAMFILES%\Veeam\Backup and Replication\Enterprise Manager\Veeam.EM.DB.Migration.exe |

* On Linux-based machine:

|  |
| --- |
| /opt/veeam/vbem/Veeam.EM.DB.Migration.dll |

To migrate Enterprise Manager, follow these steps:

1. On the Microsoft Windows machine, back up the Enterprise Manager configuration database to an EMCO backup file. To create a configuration backup, use the Veeam.EM.DB.Migration.exe application. The utility requires access to the registry so you must run the command-line shell as administrator. In addition, make sure that the account that you specify to authenticate against a PostgreSQL server is a superuser.

|  |
| --- |
| Veeam.EM.DB.Migration.exe /file:"C:\em\_configuration.emco" /backupemdatabase /encryptionpassword:Password01 /encryptionhint:thatpassword |

1. Transfer the backup file to the Linux machine where Enterprise Manager is deployed as part of Veeam Software Appliance:

1. To enable SSH connection on the Linux machine, use Veeam Host Management. For details, see [Configuring Remote Access Settings](hmc_configure_remote_access.md#access_ssh).
2. To transfer the backup file, you can run, for example, the scp command on the Microsoft Windows machine:

|  |
| --- |
| scp "C:\em\_configuration.emco" veeamadmin@em.example.com:/tmp/em\_configuration.emco |

1. Restore the configuration database on the Linux machine:

1. To request root access on the Linux machine, use Veeam Host Management. For details, see [Configuring Remote Access Settings](hmc_configure_remote_access.md#access_root_shell).
2. To restore the configuration database from the backup file, run the Veeam.EM.DB.Migration.dll application with the dotnet command:

|  |
| --- |
| # dotnet /opt/veeam/vbem/Veeam.EM.DB.Migration.dll /file:"/tmp/em\_configuration.emco" /restoreemdatabase /encryptionpassword:'Password01' |

1. Update the configuration database name in the configuration file /etc/veeam/veeam\_backup\_reporting.conf:

|  |
| --- |
| [DatabaseConfigurations]  SqlActiveConfiguration=PostgreSql  [DatabaseConfigurations\MsSql]  [DatabaseConfigurations\PostgreSql]  SqlDatabaseName=VeeamBackupReporting\_00 |

1. To apply the changes, restart all Enterprise Manager services using Veeam Host Management. For details, see [Performing Maintenance Tasks](hmc_perform_maintenance_tasks.md).
2. To enable Enterprise Manager to collect data from added backup servers, re‑enter credentials for each added backup servers. For details, see [Editing Backup Servers](editing_backup_server.md).

Utility Parameters

The table below describes the Veeam.EM.DB.Migration parameters that you can use to migrate Enterprise Manager from Microsoft Windows to Linux.

| Parameter | Description |
| --- | --- |
| /? | Displays help. |
| /file:<value> | Specifies file name and location of an EMCO backup file. |
| /encryptionpassword:<value> | Specifies a password for backup file encryption. |
| /encryptionhint:<value> | Specifies a hint for the encryption password. |
| /backupemdatabase | Backs up the Enterprise Manager configuration database to an EMCO backup file. |
| /restoreemdatabase | Restores the Enterprise Manager configuration database from an EMCO backup file. |
| /initialcatalog:<value> | Specifies a name of a target PostgreSQL database. The default value is VeeamBackupReporting. If you skip the parameter, the default value is used.  If a database with the specified name (or the default name) exists, the utility adds an increment postfix to the database name, for example: VeeamBackupReporting\_00, VeeamBackupReporting\_01. |
| /verbose | Enables verbose logging mode. |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
