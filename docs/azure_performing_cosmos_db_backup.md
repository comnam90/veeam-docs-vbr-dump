---
title: "Performing Cosmos DB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_cosmos_db_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Cosmos DB Backup


|  |
| --- |
| Important |
| Cosmos DB backup is available only for backup appliances managed by a Veeam Backup & Replication server. To unlock the full functionality, you must [install Veeam Plug-in for Microsoft Azure on the server](azure_deploying_vb.md) and [add your appliances](azure_adding_appliance_console.md) to the backup infrastructure. |

One backup policy can be used to process one or more Cosmos DB accounts within one Microsoft Entra tenant. The scope of data that you can protect in a tenant is limited by permissions of a service account that is specified in the backup policy settings.

Before you create a Cosmos DB backup policy, check the following prerequisites:

* If you plan to enable backup to repository, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [repositories](azure_repositories.md) and [worker instances](azure_workers.md).
* If you plan to receive email notifications on backup policy results, configure email notification settings first. For more information, see [Configuring Global Notification Settings](azure_configuring_notification_settings.md).

To schedule data protection tasks to run automatically, [create backup policies](azure_cosmos_db_backup_create.md). For each protected Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account, you can also [take a backup to a repository manually](azure_creating_cosmos_db_backups_manually.md) when needed.

|  |
| --- |
| Important |
| Consider the following:   * Veeam Backup for Microsoft Azure allows you to protect only Cosmos DB accounts created using the following APIs: NoSQL, MongoDB RU-based, Apache Gremlin, Table and PostgreSQL. * Veeam Backup for Microsoft Azure does not support protecting Cosmos DB accounts that have [periodic backup](https://learn.microsoft.com/en-us/azure/cosmos-db/periodic-backup-restore-introduction) or [multi-region writes](https://learn.microsoft.com/en-us/azure/cosmos-db/how-to-manage-database-account#configure-multiple-write-regions) enabled. |

Page updated 2026-02-12

