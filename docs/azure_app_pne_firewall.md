---
title: "Configuring Firewall Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_firewall.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Configuring Firewall Settings


To configure firewall rules for a storage account in which Azure resources that you want to protect reside, do the following:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Click More services and select Resource groups on the All services page.
3. On the Resource groups page, select the resource group to which the necessary storage account belongs. The resource group page will open.
4. In the Resource list, locate and click the storage account. The Storage account page will open.
5. Navigate to Security + networking > Networking.
6. On the Firewalls and virtual networks tab, choose the Enabled from selected virtual networks and IP addresses option and click Add existing virtual network.
7. In the Add networks window:

1. From the Subscription drop-down list, select an Azure subscription to which Azure VM hosting Veeam Backup for Microsoft Azure belongs.

1. From the Virtual networks drop-down list, select check boxes next to necessary virtual networks:

* To allow Veeam Backup for Microsoft Azure to manage backup repositories and to back up Azure VMs, select VNets to which the backup appliance and worker instances are connected.
* To allow Veeam Backup for Microsoft Azure to back up Azure file shares, select the VNet to which the backup appliance is connected.

1. From the Subnets drop-down list, select check boxes next to subnets to which the backup appliance or worker instances are connected.

|  |
| --- |
| Note |
| To allow access from virtual networks to storage accounts, Microsoft Azure uses virtual network service endpoints. If any of the selected networks do not have virtual network service endpoints enabled for Microsoft.Storage.Global, Microsoft Azure will raise a warning. In this case, click Enable and wait for the process to complete. For more information on virtual network service endpoints, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview). |

1. Click Add.

1. Click Save.

Page updated 2024-09-19

