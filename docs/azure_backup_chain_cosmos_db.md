---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_chain_cosmos_db.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


If you enable backup to a repository for a backup policy, the backup appliance creates a new backup for the database of each processed Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account in a standard repository during every backup session. A sequence of backups created during a set of backup sessions makes up a regular backup chain.

Each Cosmos DB for PostgreSQL or Cosmos DB for MongoDB backup in the backup chain contains metadata that stores information about the protected instance, the backup policy that created the backup, as well as the date, time and configured retention settings. Veeam Backup for Microsoft Azure uses metadata to identify outdated backups, to retrieve information on the source database configuration during recovery operations, and so on.

|  |
| --- |
| Note |
| The [forever forward incremental backup](azure_backup_chain_vm.md) method is not implemented for Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts — during every backup session, Veeam Backup for Microsoft Azure creates a full backup in the regular backup chain. |

The period of time during which Cosmos DB for PostgreSQL and Cosmos DB for MongoDB backups are kept in the backup chain is defined by retention policy settings. For details, see [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md).

Related Topics

* [Archive Backup Chain](azure_archive_chain_cosmos_db.md)
* [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md)

Page updated 2026-07-01

