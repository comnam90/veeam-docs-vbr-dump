---
title: "Creating Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_policy_add_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Policies


You can create backup policies in the backup appliance Web UI only. However, you can launch the Add Policy wizard directly from the Veeam Backup & Replication console — to do that, use either of the following options:

* Switch to the Home tab, click Backup Job on the ribbon, navigate to Microsoft Azure > VM, SQL, File share or Cosmos DB, and select the backup appliance on which you want to create the backup policy.
* Open the Home view, right-click Jobs, navigate to Backup > Microsoft Azure > VM, SQL, File share or Cosmos DB, and select the backup appliance on which you want to create the backup policy.

Veeam Backup & Replication will open the Add VM Policy, Add Azure SQL Policy, Add Azure Files Policy or Add Cosmos DB Policy wizard in a web browser. Complete the wizard as described in sections [Creating VM Backup Policies](azure_vm_backup_name.md), [Creating SQL Backup Policies](azure_sql_backup_name.md), [Creating Azure Files Backup Policies](azure_fs_backup_name.md) or [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_name.md).

[![Create Azure policy](images/azure_policy_create.webp)](images/azure_policy_create.webp "Create Azure policy")

Page updated 2026-07-01

