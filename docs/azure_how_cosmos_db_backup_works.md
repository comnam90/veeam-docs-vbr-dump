---
title: "Cosmos DB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_how_cosmos_db_backup_works.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Cosmos DB Backup


When processing a Cosmos DB account added to a backup policy, Veeam Backup for Microsoft Azure uses continuous backup — a native Microsoft Azure capability that allows you to eliminate consumption of extra provisioned throughput without affecting the database performance and availability.

Every 8 hours, Veeam Backup for Microsoft Azure runs configuration sessions to check the continuous backup retention period defined in Microsoft Azure for all the Cosmos DB accounts added to the backup scope. If the retention period differs from the retention period specified in the backup policy settings, Veeam Backup for Microsoft Azure redefines the retention period in Microsoft Azure.

Every time Veeam Backup for Microsoft Azure synchronizes data between Microsoft Azure and the configuration database, it creates a database record for each Cosmos DB account added to a backup policy — the record can further be used to restore this account. For more information on how continuous backup is performed, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/cosmos-db/continuous-backup-restore-introduction).

Backup to Repository

If you enable backup to a repository, Veeam Backup for Microsoft Azure performs the following steps:

1. Launches a worker instance in an Azure region where the processed Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account reside.

By default, Veeam Backup for Microsoft Azure launches worker instances using virtual networks created automatically. However, you can add specific worker configurations. For more information, see [Managing Worker Instances](azure_worker_configurations.md).

1. Synchronizes data between the backup repository and the configuration database to ensure data consistency.
2. Uses the worker instance to create a backup file of user data contained in the database, transfers the data to the target backup repository and stores it in the native Veeam format.

|  |
| --- |
| Note |
| Veeam Backup for Microsoft Azure does not include any metadata such as credentials in the backup file. |

1. Deallocates the worker instance when the backup session completes.

1. If you enable the [backup archiving mechanism](azure_archive_chain_cosmos_db.md), Veeam Backup for Microsoft Azure performs the following operations:

1. Launches a worker instance in an Azure region in which the target backup repository resides.
2. Retrieves data from the backup repository and transfers it to the target archive repository.
3. Deallocates the worker instance when the archive session completes.

Related Topics

[Backup Chain](azure_backup_chain_cosmos_db.md)

Page updated 2025-06-06

