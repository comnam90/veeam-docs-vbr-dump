---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_proxy_byb.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you configure an Azure restore proxy appliance, check the following prerequisites:

* You must add information about your Microsoft Azure Compute account to Veeam Backup & Replication. For more information, see [Adding Microsoft Azure Compute Accounts](restore_azure_accounts.md).
* You must configure the following objects in Microsoft Azure beforehand:

+ Storage account whose resources will be used to deploy the Azure restore proxy appliance.
+ Networks to which you plan to connect the Azure restore proxy appliance.

For storage accounts and network configuration, you must use the same deployment model that you plan to use for Azure restore proxy appliance creation.

|  |
| --- |
| Important |
| When you deploy Azure restore proxy appliance for Azure Stack Hub, make sure that Windows Server 2019 is available in Azure marketplace. |


