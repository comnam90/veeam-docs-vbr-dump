---
title: "Cosmos DB Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_restore_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Cosmos DB Restore


Veeam Plug-in for Microsoft Azure offers the following restore operations:

* Point-in-time restore — restores an entire Cosmos DB account or its specific items using the native Microsoft Azure [point-in-time restore](https://learn.microsoft.com/en-us/azure/cosmos-db/restore-account-continuous-backup) feature. You can restore Cosmos DB account data to the most recent or to any available point in time (timestamp).

To restore a Cosmos DB account to a restorable timestamp, Veeam Backup for Microsoft Azure sends REST API requests to Microsoft Azure to create a new Cosmos DB account with the configuration specified in the restore settings.

* Restore from repository — restores the database of a specific Cosmos DB for PostgreSQL account or databases and collections of a specific Cosmos DB for MongoDB account from a backup stored in a repository. You can restore the database data to the most recent state or to any available restore point.

To restore an item of a Cosmos DB account from a backup, Veeam Backup for Microsoft Azure performs the following steps:

1. [Applies only if you perform restore from an archived backup] Retrieves data from the archived restore point.
2. Launches a worker instance in an Azure region where the target Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account to which the item will be restored resides.
3. Uses the worker instance to retrieve user data contained in the backup, and then imports this data to the target Cosmos DB account.
4. Deallocates the worker instance.

To learn how to restore a Cosmos DB account to a restorable timestamp, see [Performing Point-in-time Restore](azure_cosmos_db_restore_point_in_time.md). To learn how to restore the database of a Cosmos DB for PostgreSQL account or databases and collections of a Cosmos DB for MongoDB account from a backup, see [Performing Restore From Repository](azure_cosmos_db_restore_from_repository.md).

Page updated 2026-07-01

