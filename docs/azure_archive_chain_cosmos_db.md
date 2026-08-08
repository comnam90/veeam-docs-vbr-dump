---
title: "Archive Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_archive_chain_cosmos_db.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Archive Backup Chain


If you enable backup archiving for a backup policy, the backup appliance creates a new backup in an archive repository during every archive session. A sequence of backups created during a set of archive sessions makes up an archive backup chain.

|  |
| --- |
| Note |
| The forever forward incremental backup method is not implemented for Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts — during every archive session, Veeam Backup for Microsoft Azure creates a full backup in the regular backup chain (that is, every incremental backup contains the full database data set). |

The period of time during which Cosmos DB for PostgreSQL and Cosmos DB for MongoDB backups are kept in the archive backup chain is defined by retention policy settings. For details, see [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md).

Page updated 2026-07-01

