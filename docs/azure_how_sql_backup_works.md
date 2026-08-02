---
title: "SQL Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_how_sql_backup_works.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# SQL Backup


When processing an Azure SQL database added to a backup policy, Veeam Backup for Microsoft Azure can create a restore point of the database and transfer the point directly to a backup repository, or Veeam Backup for Microsoft Azure can copy the database to a staging server first, create a restore point and then transfer the point to a repository. In the latter case, Veeam Backup for Microsoft Azure creates a transactionally consistent backup. This guarantees the consistency of the database state during recovery but can increase costs associated with cross-region data transfer.

Veeam Backup for Microsoft Azure performs SQL backup in the following way:

1. [Applies only if you perform backup using a staging server] Depending on the type of the processed Azure SQL database, Veeam Backup for Microsoft Azure does the following:

* For an Azure SQL database residing on a SQL Server — creates a copy of the source database on the staging server using the Azure REST API.
* For a database residing on an Azure SQL Managed Instance — creates a copy of the source database on the staging server using point-in-time restore (PITR). For more information on Azure point-in-time restore, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-sql/managed-instance/point-in-time-restore?tabs=azure-portal).

For more information on the Azure SQL family of SQL Server database engine products, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-sql/?view=azuresql).

1. Launches a worker instance in an Azure region where the staging server or the source database resides.

1. Synchronizes data between the backup repository and the configuration database to ensure data consistency.
2. Exports the database schema, indexes and constraints to a BACPAC file. For more information on BACPAC files, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-ver15#bacpac).

|  |
| --- |
| Important |
| BACPAC export of databases with external references is not supported. If a SQL database was migrated to an Azure SQL Database Server or Azure SQL Managed Instance, make sure to clear legacy references, orphaned database users and credentials set up with authentication types not supported by Azure SQL, to avoid BACPAC export errors. |

1. Reads data from the exported BACPAC file on the worker instance, transfers the data to the target backup repository and stores it in the native Veeam format.

1. [Applies only if you perform backup using a staging server] Removes the copy of the source database from the staging server.
2. Deallocates the worker instance when the backup session completes.
3. If you enable the [backup archiving mechanism](azure_sql_backup_archiving.md), Veeam Backup for Microsoft Azure performs the following operations:

1. Launches a worker instance in an Azure region in which the target backup repository resides.
2. Retrieves data from the backup repository and transfers it to the target archive repository.
3. Deallocates the worker instance when the archive session completes.

Related Topics

[Backup Chain](azure_backup_chain_sql.md)

Page updated 2025-11-28

