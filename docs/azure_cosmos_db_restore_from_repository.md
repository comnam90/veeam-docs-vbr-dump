---
title: "Performing Restore From Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_restore_from_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore From Repository


In case a disaster strikes, you can restore the database of a Cosmos DB for PostgreSQL account or databases and collections of a Cosmos DB for MongoDB account from a backup stored in a repository. Veeam Plug-in for Microsoft Azure allows you to restore one database at a time, to the original or to a new location.

Before You Begin

Consider the following prerequisites:

* To restore a database from a backup that is stored in an archive repository, you must retrieve the archived data first. You can either retrieve the archived data manually before you begin the restore operation, or launch the data retrieval process right from the restore wizard. To learn how to retrieve data manually, see [Retrieving Data from Archive](azure_retrieving_cosmos_db_data.md).
* If you plan to restore databases and collections of a Cosmos DB for MongoDB account, make sure that the MongoDB version of the target account to which you want to restore the data is not earlier than the MongoDB version of the source account that originally managed these databases and collections.

How to Perform Cosmos DB Restore

To restore the database of a Cosmos DB for PostgreSQL account or databases and collections of a Cosmos DB for MongoDB account, do the following:

1. [Launch the Cosmos DB Restore wizard](azure_cosmos_db_restore_from_repository_wizard.md).
2. [Select a restore point](azure_cosmos_db_restore_from_repository_point.md).
3. [Select a service account](azure_cosmos_db_restore_from_repository_service_account.md).
4. [Specify data retrieval settings](azure_cosmos_db_restore_from_repository_retrieve.md).
5. [Configure restore settings](azure_cosmos_db_restore_from_repository_settings.md).
6. [Specify a restore reason](azure_cosmos_db_restore_from_repository_reason.md).
7. [Finish working with the wizard](azure_cosmos_db_restore_from_repository_finish.md).

Page updated 2026-07-01

