---
title: "Removing Cosmos DB Backups Created Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_cosmos_db_manual_backups.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing Cosmos DB Backups Created Manually


To remove all backups created for a Cosmos DB for PostgreSQL or Cosmos DB for MongoDB account manually, follow the instructions provided in [Removing Cosmos DB Backups](azure_removing_cosmos_db_backups.md). If you want to remove a specific image-level backup created manually, do the following:

1. Navigate to Protected Data > Databases > Cosmos DB.
2. Select the check box next to the necessary Cosmos DB account, and click the link in the Restore Points column.
3. In the Available Restore Points window, select the necessary restore point and click Remove Manual Backup.

[![Removing Cosmos DB Backups Created Manually](images/azure_removing_cosmos_db_manual_backups.webp)](images/azure_removing_cosmos_db_manual_backups.webp "Removing Cosmos DB Backups Created Manually")

Related Topics

[Creating Cosmos DB Backups Manually](azure_creating_cosmos_db_backups_manually.md)

Page updated 2025-03-25

