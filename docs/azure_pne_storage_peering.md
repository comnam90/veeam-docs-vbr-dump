---
title: "Step 8. Configure Private Endpoint Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_storage_peering.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 8. Configure Private Endpoint Network Settings


To allow Veeam Backup for Microsoft Azure components to communicate in private environment, you must configure peering connections between the VNet to which the backup appliance is connected and the VNet to which the newly created private endpoint is connected.

To create a peering, perform the following steps:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Open the Resource group page.
3. In the Resource list, locate and click the VNet to which the backup appliance is connected. The Virtual network page will open.
4. Navigate to Settings > Peerings.
5. Click Add to open the Add peering page.
6. On the Add peering page, specify the following settings:

1. In the This virtual network section, specify a name for the peering link that will be added to the VNet to which the backup appliance is connected. Leave the default settings for the other options in this section.
2. In the Remote virtual network section, specify a name for the peering link that will be added to the target VNet. Leave the default settings for the other options in this section.
3. From the Subscription drop-down list, select an Azure subscription to which worker instances belong.

1. From the Virtual networks drop-down list, select the virtual network to which worker instances are connected.
2. Click Add.

[![Peering Virtual Networks](images/azure_vnet_peering.webp)](images/azure_vnet_peering.webp "Peering Virtual Networks")

Page updated 2024-08-26

