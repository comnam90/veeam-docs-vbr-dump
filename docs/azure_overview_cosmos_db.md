---
title: "Protecting Cosmos DB Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_overview_cosmos_db.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Cosmos DB Accounts


To produce backups of Cosmos DB accounts, the backup appliance runs backup policies. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

By default, Veeam Plug-in for Microsoft Azure does not install agent software to back up Cosmos DB account data — it uses native Microsoft Azure capabilities instead. Every time Veeam Backup for Microsoft Azure synchronizes data between Microsoft Azure and the configuration database, it creates a database record for each Cosmos DB account added to a backup policy. You can also instruct Veeam Backup for Microsoft Azure to create backups of the processed Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts. For more information on how Cosmos DB backup works, see [Cosmos DB Backup](azure_how_cosmos_db_backup_works.md).

How To Protect Cosmos DB Accounts

To create a Cosmos DB backup policy, perform the following steps:

1. [Check limitations and prerequisites](azure_limitations.md#backup).
2. [Specify service accounts to access Azure services and resources](azure_service_accounts.md).
3. [[Optional] Add backup repositories to store backed-up data](azure_repositories.md).
4. [[Optional] Configure worker instance settings to launch workers while processing Cosmos DB data](azure_workers.md).
5. [[Optional] Configure global retention settings for obsolete session records](azure_configuring_global_retention.md).
6. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](azure_configuring_notification_settings.md).
7. [Complete the Add Cosmos DB Policy wizard](azure_cosmos_db_backup_wizard.md).

Related Topics

[Cosmos DB Restore](azure_cosmos_db_restore_hiw.md)

Page updated 2026-07-01

