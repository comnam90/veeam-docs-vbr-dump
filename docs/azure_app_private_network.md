---
title: "Working in Private Environments"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_private_network.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Working in Private Environments


For Veeam Backup for Microsoft Azure to be able to work with Azure resources that operate in private environments, do the following:

1. Switch to the Configuration page, navigate to General > Deployment Mode and set the Private network deployment toggle to On.
2. Set the Create service endpoints toggle to On, or configure the virtual network service endpoint manually in Microsoft Azure as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview).
3. Click Save.

Additionally, there is a list of configuration actions that must be performed both on the Veeam Backup for Microsoft Azure and the client side.

Actions Performed by Veeam Backup for Microsoft Azure

Veeam Backup for Microsoft Azure will automatically configure network settings required:

* To allow secure communication between the backup appliance and storage accounts where Veeam applications and scripts are stored.

Veeam Backup for Microsoft Azure creates these accounts in Azure regions where worker instances are launched and protected VMs with VSS agents reside.

* To allow the Azure Queue Storage messaging service to transfer data between services in private virtual networks.

Actions Performed by Client

|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see Microsoft Docs. |

To back up and restore Azure resources operating within private virtual networks (VNets), you must grant Veeam Backup for Microsoft Azure access to these resources. To do that, configure specific network settings to allow traffic from VNets to which the backup appliance and worker instances are connected to reach your resources. Depending on the Azure resource to which you want to grant access, do either of the following:

* [Configure network settings for an Azure VM](azure_app_pne_vm_backup.md).
* [Configure network settings for a SQL Server](azure_app_pne_sql.md).
* [Configure network settings for a SQL Managed Instance](azure_app_pne_managed_instance.md).
* [Configure network settings for a Cosmos DB account](azure_app_pne_cosmos_db.md).
* [Configure network settings for a repository, an unmanaged Azure VM or an Azure file share](azure_app_pne_storage_account.md).

Page updated 2025-09-02

