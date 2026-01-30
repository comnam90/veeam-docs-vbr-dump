---
title: "Configuring Helper Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_helper.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Configuring Helper Appliances


Before you configure helper appliances, consider the following:

* Veeam Backup & Replication uses its built-in credentials record to work with all helper appliances. For security reasons, we recommended that you change a password for this account before you set up the helper appliances. Changing credentials is required only once. For more information, see [Changing Credentials for Helper Appliances](restore_azure_credentials.md).
* If you plan to restore Linux workloads to different locations, you must configure a helper appliance in each location to which workloads will be restored.

Helper appliances are configured when you add a Microsoft Azure compute. For more information, see the Helper Appliance step description in the [Microsoft Azure Compute Accounts](restore_azure_accounts.md) section.


