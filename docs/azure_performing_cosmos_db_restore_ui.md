---
title: "Performing Cosmos DB Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_cosmos_db_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Cosmos DB Restore Using Web UI


Veeam Plug-in for Microsoft Azure offers the following restore options:

* [Point-in-time restore](azure_cosmos_db_restore_point_in_time.md) — restores a Cosmos DB account from a timestamp to a new location.
* [Restore from repository](azure_cosmos_db_restore_from_repository.md) — restores the database of a Cosmos DB for PostgreSQL account or databases and collections of a Cosmos DB for MongoDB account from a backup stored in a repository to the original or to a new location.

|  |
| --- |
| Important |
| Consider the following:   * Due to Microsoft Azure limitations, Veeam Plug-in for Microsoft Azure does not support restore of Cosmos DB accounts encrypted using customer-managed keys. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/cosmos-db/how-to-setup-customer-managed-keys?tabs=azure-portal). * Due to Microsoft Azure limitations, when restoring a Cosmos DB for PostgreSQL account that has the geo-redundant backup capability enabled, you can restore this account to its primary region only. Consider that the restored account will have the capability disabled, and you will not be able to change this setting for the account. For more information, see [Microsoft Docs](https://azure.microsoft.com/en-us/updates/general-availability-azure-cosmos-db-for-postgresql-georedundant-backup-and-restore/#:~:text=Geo%2Dredundant%20backup%20for%20Azure,be%20enabled%20during%20cluster%20provisioning.). |

You can restore Cosmos DB data to the most recent state or to any available restore point.

Page updated 2026-07-01

