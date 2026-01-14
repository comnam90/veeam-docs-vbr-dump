---
title: "Managing Azure Restore Proxy Appliances"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_proxy.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# Managing Azure Restore Proxy Appliances

In this article

Azure restore proxy appliances (former Azure proxies) are Windows-based VMs over which Veeam Backup & Replication transports VM disk data to Blob storage. Veeam Backup & Replication uses Azure restore proxy appliances during restore of Windows-based and Linux-based workloads.

Azure restore proxy appliances help speed up the restore process especially if you restore workloads to a distant location or the network connection is slow. Veeam components installed on an Azure restore proxy appliance compress and deduplicate disk data, which helps reduce network traffic.

Although Azure restore proxy appliances are optional, we recommend you to configure them. Azure restore proxy appliances do not require a lot of resources but can significantly improve restore performance. Configure an Azure restore proxy appliance in a location to which you plan to restore workloads or close to this location. If you plan to restore workloads to different locations, configure at least one Azure restore proxy appliance in each location.

The process of Azure restore proxy appliance deployment takes some time. We recommend you to configure the Azure restore proxy appliance in advance, before you start the restore process. To configure an Azure restore proxy appliance, use the New Azure Restore Proxy Appliance wizard as described in section [Configuring Azure Restore Proxy Appliances](restore_azure_proxy_config.md). Veeam Backup & Replication will deploy a Microsoft Windows Server machine in Microsoft Azure and will assign the role of the Azure restore proxy appliance to this machine. You can then instruct Veeam Backup & Replication to use the Azure restore proxy appliance for restore tasks.

The Azure restore proxy appliance is persistent. After the restore process finishes, the Azure restore proxy appliance gets powered off and remains in Microsoft Azure. The Azure restore proxy appliance remains in the powered off state until a new restore process is started. Note that Microsoft Azure will bill you for storing Azure restore proxy appliance disks in the storage account. To remove an Azure restore proxy appliance, follow the instruction provided in [Removing Azure Restore Proxy Appliances](restore_azure_remove_proxy.md).

In This Section

* [Configuring Azure Restore Proxy Appliances](restore_azure_proxy_config.md)
* [Removing Azure Restore Proxy Appliances](restore_azure_remove_proxy.md)

Page updated 3/11/2025

Page content applies to build 13.0.1.1071
