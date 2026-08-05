---
title: "Step 3. Select Service Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_restore_ui_service_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Select Service Account


At the Account step of the wizard, select a service account whose permissions the backup appliance will use to perform the restore operation.

1. Click Choose account.
2. In the Choose service account window, select the necessary account and click Apply. The specified service account must be assigned permissions listed in section [Azure SQL Permissions](azure_sql_permissions.md#restore).

For a service account to be displayed in the list of available accounts, it must be added to the backup appliance and assigned the Azure SQL Restore operational role as described in section [Adding Service Accounts](azure_service_account_add.md). If you have not added the necessary service account to the backup appliance beforehand, you can do it without closing the SQL Database Restore wizard. To do that, click Add and complete the Add Account wizard.

[![Performing SQL Restore](images/azure_sql_restore_account.webp)](images/azure_sql_restore_account.webp "Performing SQL Restore")

Page updated 2026-07-01

