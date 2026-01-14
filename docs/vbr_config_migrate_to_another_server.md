---
title: "Migrating Configuration Database to Another SQL Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_migrate_to_another_server.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Migrating Configuration Database to Another SQL Server

In this article

It is the best practice to keep the Veeam Backup & Replication application and its configuration database on the same server to maintain lowest latency and highest performance. However, in some scenarios a remote Microsoft SQL Server instance can be the better choice:

* High Availability. SQL Clustering and Always On Availability Group on external SQL Servers can be used for high availability of the configuration database. To learn about the configuration details, see [this Veeam KB article](https://www.veeam.com/kb2301).
* Licensing. Some enterprises have dedicated virtual clusters for SQL Servers due to licensing constraints. In such cases, you can place the Veeam configuration database on an existing instance to lower the total cost of ownership.

If you need to migrate the Veeam Backup & Replication configuration database to another SQL server, you can connect the configuration database to a Microsoft SQL Server instance deployed on another server and restore the configuration settings from the backup. As a result, you will be able to continue using the same Veeam Backup & Replication server but it will be connected to a configuration database on another server.

Limitations and Considerations

Before you migrate the configuration database of Veeam Backup & Replication to another SQL server, consider the following limitations and considerations:

* This section gives instructions on how to migrate a configuration database to another SQL server. If you need to migrate the Veeam Backup & Replication application itself, see [Migrating Veeam Backup & Replication to Another Backup Server](vbr_config_migrate.md).
* It is recommended that you use Veeam Backup & Replication tools to create configuration backups and migrate the configuration database. If you use native Microsoft SQL Server tools or others, after migration, some information, such as secure configuration data, may not be accessible.
* If you are migrating the configuration database to a remote SQL instance that uses Windows Authentication, all services that had access to the remote SQL instance before a migration must have the these permissions after migration. For more information on permissions, see [Permissions](required_permissions.md#sqloperation).
* The account used to run Veeam Backup Service requires access to the database. For more information see, [Permissions](required_permissions.md#sqloperation).
* If a backup server and a configuration database are located in different AD domains, the AD domain where the configuration database is located must have a trust relationship with the AD domain to which the backup server is added.
* When you migrate the configuration database to another SQL server, you must use the Microsoft SQL Server credentials that have CREATE ANY DATABASE permission on the target Microsoft SQL Server. For details, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver15). After database creation this account automatically gets the db\_owner role and can perform all operations with the database. If the current account does not have this permission, a Database Administrator may create an empty database in advance and grant the db\_owner role to the account that will be used for migration of the configuration database.
* Veeam Backup Enterprise Manager collects data from backup servers with configuration databases that run on the same database engine as the Enterprise Manager configuration database. The database engine used by Veeam Backup Enterprise Manager and all of the Veeam Backup & Replication Servers managed by this Veeam Backup Enterprise Manager must match. To migrate the Enterprise Manager configuration database, see [Veeam Backup Enterprise Manager Guide](https://helpcenter.veeam.com/docs/vbr/em/em_db_migration.html?ver=13).

Migrating Configuration Database

If you want to migrate the configuration database of Veeam Backup & Replication to another SQL server, perform the following steps:

1. [Stop and disable jobs](#step1).
2. [Back up the configuration database](#step2).
3. [Restore the configuration database from the backup](#step3).
4. [[Optional] Reactivate the Enterprise Manager Keyset](#step4).
5. [Finish the configuration](#step5).

Step 1. Stop and Disable Jobs

Before you start the database migration, you must finish all jobs and restore sessions. If the job is scheduled, you must disable the job. For instructions on how to stop and disable jobs, see [Managing Backup Jobs](managing_jobs.md).

|  |
| --- |
| Note |
| Do not start or enable any jobs until the migration of Veeam Backup & Replication is finished. If you start a job before migration is completed, Veeam Backup & Replication will produce a new restore point in the chain and update the chain metadata. The created configuration backup will not contain information about this new restore point. When you migrate data from the configuration backup to the database and start the job again, Veeam Backup & Replication will fail to synchronize the metadata of the backup chain with data in the database. As a result, the job will fail. |

Step 2. Create Configuration Database Backup

To create a configuration database backup manually, perform the following steps:

1. From the main menu of the Veeam Backup & Replication console, select Configuration Backup.
2. Make sure that the Enable configuration backup to the following repository check box is selected.
3. From the list of repositories, select a backup repository in which the configuration backup must be stored.
4. Click Backup now.

![Migrating Configuration Database to Another SQL Server](images/migrating_config_db_backup.webp)

|  |
| --- |
| Note |
| Loss protection disabled warning is safe to ignore if you do not have Veeam Backup Enterprise Manager installed, your backup server is not registered with Veeam Backup Enterprise Manager server, or your system administrator chose not to enable loss protection functionality. |

Step 3. Restore Configuration Database from Backup

Before you start the restore process, check the [prerequisites](restore_vbr_before_you_begin.md). To restore the configuration database, perform the following:

1. From the main menu of the Veeam Backup & Replication console, select Configuration Backup.
2. In the Restore section, click Restore.

[![Migrating Configuration Database to Another SQL Server](images/migrating_config_db_restore.webp)](images/migrating_config_db_restore.webp)

1. At the Restore Mode step of the Veeam Backup & Replication Configuration Restore wizard, select Migrate.

[![Migrating Configuration Database to Another SQL Server](images/vbr_config_restore_mode.webp)](images/vbr_config_restore_mode.webp)

1. Complete the wizard as described in section [Restoring Configuration Database](restore_vbr_source.md).

Step 4. [Optional] Reactivate Enterprise Manager Keyset

After you migrate the Veeam Backup & Replication configuration database to another server, Veeam Backup Enterprise Manager still sees the Veeam Backup & Replication server. However, you may need to reactivate encryption keys.

If you use the [Data Encryption](data_encryption.md) feature to encrypt backups and your Veeam Backup & Replication server is added to the Veeam Backup Enterprise Manager infrastructure, then you must reactivate the Enterprise Manager keyset.

To reactivate the Enterprise Manager key, perform the following steps:

1. In the Veeam Backup Enterprise Manager web console, open the Settings section of the Configuration view.
2. Open the Key Management tab.
3. In the Managed keys section, select the necessary keyset and click Activate.

For detailed instructions, see the [Activating Enterprise Manager Keyset](https://helpcenter.veeam.com/docs/vbr/em/em_activate_em_keys.html?ver=13) section in the Veeam Backup Enterprise Manager Guide.

Step 5. Finish Configuration

After restoring the configuration database from the backup, finalize the configuration:

* Configure all necessary settings to ensure that you have a working configuration database backup. You can now perform a backup of your new configuration database in the Configuration Backup Settings window.

Reschedule your configuration database backup. Also, check if you can see the Loss protection enabled label.

* If you have local repositories, after migration to another VM they may be displayed as empty. In this case, add them again and remap the jobs.

* Enable your backup jobs and backup copy jobs. Take a closer look at your backup infrastructure to ensure that everything is working as expected.

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
