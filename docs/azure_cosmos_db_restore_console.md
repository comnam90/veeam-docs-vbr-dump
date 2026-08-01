---
title: "Performing Cosmos DB Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_restore_console.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Performing Cosmos DB Restore Using Console


Veeam Backup & Replication allows you to restore an entire Cosmos DB account or its specific items from a restorable timestamp, or to restore the database of a Cosmos DB for PostgreSQL or a Cosmos DB for MongoDB account from a backup stored in a repository. To learn how Cosmos DB restore works, see [Cosmos DB Restore](azure_cosmos_db_restore_hiw.md).

Point-in-time Restore

To restore a Cosmos DB account from a restorable timestamp, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects the Cosmos DB account you want to restore, select the account and click Microsoft Azure Cosmos DB on the ribbon.

Alternatively, you can right-click the selected subscription and click Restore to Microsoft Azure Cosmos DB.

Veeam Backup & Replication will open the Cosmos DB Restore wizard in a web browser. Complete the wizard as described in section [Performing Point-in-time Restore](azure_cosmos_db_restore_point_in_time.md).

[![Performing Cosmos DD Point-in-time Restore Using Console](images/azure_restore_cosmos_db_pitr_console.webp)](images/azure_restore_cosmos_db_pitr_console.webp "Performing Cosmos DD Point-in-time Restore Using Console")

Restore From Repository

To restore the database of a Cosmos DB for PostgreSQL or a Cosmos DB for MongoDB account from a backup stored in a repository, do the following:

1. In the Veeam Backup & Replication console, open the Home view.

1. Navigate to Backups > External Repository or, to retrieve a backup stored in an archive repository, navigate to Backups > External Repository (Archive).
2. Expand the backup policy that protects the database you want to restore, select the Cosmos DB account managing the database and click Microsoft Azure Cosmos DB on the ribbon.

Alternatively, you can right-click the selected subscription and click Restore to Microsoft Azure Cosmos DB.

Veeam Backup & Replication will open the Cosmos DB Restore wizard in a web browser. Complete the wizard as described in section [Performing Restore From Repository](azure_cosmos_db_restore_from_repository.md).

[![Performing Cosmos DD Restore From Repository Using Console](images/azure_restore_cosmos_db_from_repository_console.webp)](images/azure_restore_cosmos_db_from_repository_console.webp "Performing Cosmos DD Restore From Repository Using Console")

Page updated 2025-08-25

