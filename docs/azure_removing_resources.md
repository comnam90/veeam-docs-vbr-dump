---
title: "Removing Azure Resources"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_resources.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing Azure Resources


Veeam Backup for Microsoft Azure creates a number of resources while operating in Microsoft Azure, and these resources are not removed from Microsoft Azure automatically when you uninstall the solution. That is why you must perform the following steps to remove the backup appliance and all resources created by Veeam Backup for Microsoft Azure:

1. Sign in to the Microsoft Azure portal using credentials of the Microsoft Azure account that you used to install Veeam Backup for Microsoft Azure.

1. Navigate to Resource groups and click the resource group in which the backup appliance is deployed.

1. On the resource group page, remove the Azure VM running Veeam Backup for Microsoft Azure, Azure VMs running worker instances and all resources associated with these VMs; you must also remove the storage accounts created by Veeam Backup for Microsoft Azure. To do that:

1. To remove the backup appliance, do the following:

1. In the Resources section, enter the name of the necessary VM in the search field.
2. In the Resources list, select check boxes next to the resources of the Virtual machine, Network interface, Public IP address and Disk types, and click Delete.

In the Delete Resources window, type Yes to confirm the action and click Delete.

1. To remove a worker instance, do the following:

1. In the Resources section, enter the name of the necessary VM in the search field.

1. In the Resources list, select check boxes next to the resources of the Virtual machine, Network interface and Disk types, and click Delete.

In the Delete Resources window, type Yes to confirm the action and click Delete.

1. To remove the storage accounts created by Veeam Backup for Microsoft Azure, do the following:

1. In the Resources section, enter veeam in the search field.

1. In the Resources list, select check boxes next to the resources of the Storage account type and click Delete.

In the Delete Resources window, type Yes to confirm the action and click Delete.

|  |
| --- |
| Tips |
| * You can filter resources by the Veeam backup appliance ID tag. To find all resources associated with a backup appliance, navigate to the Overview page of the appliance and click the Veeam backup appliance ID tag. * If you have specified a [custom destination](azure_worker_service_account.md) for worker instances, you will have to perform additional steps after you remove the Azure VM running Veeam Backup for Microsoft Azure. First, go back to Resource groups, click the resource group in which worker instances reside, and then repeat step 3b to remove the worker instances. |

Page updated 2025-03-21

