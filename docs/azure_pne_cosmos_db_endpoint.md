---
title: "Step 2b. Configure Private Endpoint Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_cosmos_db_endpoint.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 2b. Configure Private Endpoint Settings


At the Basics step of the Create a private endpoint wizard, do the following:

1. From the Subscription drop-down list, select an Azure subscription to which Azure VM hosting Veeam Backup for Microsoft Azure belongs.
2. From the Resource group drop-down list, select a resource group to which your newly created private endpoint will belong. You can either use an existing resource group or create a new one. For more information on creating and managing resource groups, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).
3. In the Name field, enter a name for the private endpoint.
4. From the Region drop-down list, select an Azure region of the virtual network to which the backup appliance or worker instances are connected.

For more information on the Azure regions, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/regions).

1. Click Next: Resource >.

[![Configuring Private Endpoint Settings](images/azure_app_pne_cosmos_db_endpoint.webp)](images/azure_app_pne_cosmos_db_endpoint.webp "Configuring Private Endpoint Settings")

Page updated 2024-07-01

