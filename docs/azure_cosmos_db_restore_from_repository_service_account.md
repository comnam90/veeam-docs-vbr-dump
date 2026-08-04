---
title: "Step 3. Select Service Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_restore_from_repository_service_account.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 3. Select Service Account


At the Account step of the wizard, select a service account whose permissions Veeam Backup for Microsoft Azure will use to perform the restore operation.

1. Click Choose account.
2. In the Choose account window, select the necessary account and click Apply. The specified service account must be assigned permissions listed in section [Cosmos DB Permissions](azure_cosmos_db_permissions.md#restore).

For a service account to be displayed in the list of available accounts, it must be added to Veeam Backup for Microsoft Azure and assigned the Cosmos DB Restore operational role as described in section [Adding Service Accounts](azure_service_account_add.md). If you have not added the necessary service account to Veeam Backup for Microsoft Azure beforehand, you can do it without closing the Cosmos DB Restore wizard. To do that, click Add and complete the Add Account wizard.

[![Selecting Service Account](images/azure_cosmos_db_restore_from_repository_service_account.webp)](images/azure_cosmos_db_restore_from_repository_service_account.webp "Selecting Service Account")

Page updated 2025-05-30

