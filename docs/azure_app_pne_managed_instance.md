---
title: "Configuring Network Settings for SQL Managed Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_managed_instance.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Configuring Network Settings for SQL Managed Instances


|  |
| --- |
| Important |
| Before you configure network settings for a SQL Managed Instance, disable the public endpoint for this SQL Managed Instance as described in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/public-endpoint-configure?view=azuresql&tabs=azure-portal#disable-public-endpoint). |

To allow Veeam Backup for Microsoft Azure to back up a SQL Managed Instance, you must configure the peering connection between the VNet to which worker instances are connected and the VNet to which a SQL Managed Instance is connected. To do that, perform the following steps:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Open the Resource group page.
3. In the Resource list, locate and click a virtual network to which the SQL Managed Instance is connected. The Virtual network page will open.
4. Navigate to Settings > Peering.
5. Click Add to open the Add peering page.
6. On the Add peering page, specify the following settings:

1. In the This virtual network section, specify a name for the peering link that will be added to the VNet to which the SQL Managed Instance is connected. Leave the default settings for the other options in this section.
2. In the Remote virtual network section, specify a name for the peering link that will be added to the VNet to which worker instances are connected. Leave the default settings for the other options in this section.
3. From the Subscription drop-down list, select an Azure subscription to which worker instances belong.

1. From the Virtual networks drop-down list, select the virtual network to which worker instances are connected.
2. Click Add.

Page updated 2024-04-25

