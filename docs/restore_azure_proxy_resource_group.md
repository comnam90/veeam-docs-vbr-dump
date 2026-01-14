---
title: "Step 6. Select Resource Group"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_proxy_resource_group.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# Step 6. Select Resource Group

In this article

At the Resource Group step of the wizard, you specify the resource group to which the Azure restore proxy appliance must be placed and configure DNS name label:

1. You can place the Azure restore proxy appliance to an existing or new resource group:

* Select Place VM into the existing resource group to place the Azure restore proxy appliance to an existing resource group. From the drop-down list, select the necessary resource group.
* Select Create a new resource group to create a dedicated resource group for the Azure restore proxy appliance. In the Name field, enter a name for the new resource group. The resource group name can be up to 64 characters long and can contain only alphanumeric, underscore and hyphen characters.

For the new resource group, Veeam Backup & Replication automatically creates a network security group, dynamic public IP and network interface.

1. In the DNS name label field, enter a name of the dynamic public IP. The DNS name label can be up to 80 characters long, and can contain only alphanumeric, dash and underscore characters. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/architecture/best-practices/naming-conventions).

|  |
| --- |
| Tip |
| Microsoft Azure subscriptions have default limits on the number of resource groups. If you decide to create a new resource group, make sure that you do not exceed limits of the subscription. |

![Step 6. Select Resource Group](images/azure_proxy_resource_group.webp)

Page updated 3/11/2025

Page content applies to build 13.0.1.1071
