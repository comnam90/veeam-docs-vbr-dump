---
title: "Removing Backed-Up Data"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_backups.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing Backed-Up Data


When you remove the backup appliance and all resources associated with it, backups and snapshots created by this backup appliance are not removed from your Microsoft Azure account automatically. You can later import the created Azure VM image-level backups, Azure SQL backups, Cosmos DB for PostgreSQL backups, Cosmos DB for MongoDB backups to a repository and backup copies of virtual network configurations to a new backup appliance as described in section [Adding Backup Repositories](azure_repository_add_ui.md).

If you do not want to keep the backed-up data, remove it manually as described in section [Managing Backed-Up Data](azure_managing_backups.md) before you uninstall the solution. Alternatively, you can remove the data using the Microsoft Azure portal.

|  |
| --- |
| Note |
| Consider that snapshots of Azure file shares and Azure VMs with unmanaged disks created by the Veeam backup service have no specific tags assigned. The snapshots cannot be distinguished from other snapshots of Azure file shares and Azure VMs with unmanaged disks created in Microsoft Azure. That is why we recommend to delete these snapshots from the Veeam Backup for Microsoft Azure Web UI before you uninstall the solution. |

To remove the backup data using the Microsoft Azure portal, do the following:

1. Sign in to the Microsoft Azure portal using credentials of the Microsoft Azure account that you used to install Veeam Backup for Microsoft Azure.

1. Navigate to Resource groups and click the resource group to which the backed-up data belong.
2. Remove the backed-up data:

* To remove backups, click a storage account where the backup repository storing the backed-up data resides. Navigate to Containers and select a container where the backups are stored. Select the check box next to the Veeam folder and click Delete.

* To remove cloud-native snapshots, select check boxes next to the necessary snapshots. In the Delete Resources window, type Yes to confirm the action and click Delete.

|  |
| --- |
| Important |
| If the Azure VM running Veeam Backup for Microsoft Azure resides in a resource group that contains more than one backup appliance, it is recommended that you first remove snapshots and backups created by this backup appliance, as described in section [Managing Backed-Up Data](azure_managing_backups.md). Otherwise, you will not be able to identify snapshots created by the removed backup appliance. |

Page updated 2025-03-19

