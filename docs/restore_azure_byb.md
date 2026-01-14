---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_byb.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you begin restore to Microsoft Azure, check the following prerequisites:

* Check limitations listed in section [Considerations and Limitations for Restore to Microsoft Azure](restore_azure_limitations.md).
* You must create a backup of the workload that you want to restore in Microsoft Azure. For the list of supported backups, see [Restore to Microsoft Azure](restore_azure.md#backups).
* A backup chain from which you plan to restore a workload must reside in a backup repository added to the backup infrastructure. You can also import a backup to the Veeam Backup & Replication console. For more information, see [Importing Backups Manually](importing_backups.md).

* You must configure the following objects in Microsoft Azure beforehand:

+ Storage account whose resources you plan to use to store disks of the restored workload.
+ Networks to which you plan to connect the restored workload.

* Make sure that you configured all the required components and accounts in Veeam Backup & Replication as described in section [Configuring Components and Accounts for Restore](restore_azure_setup.md).

* [For speeding up restore from Capacity Tier] It is strongly recommended to use Azure restore proxy appliance when you restore from backups residing on a Capacity Tier. For more information on Azure restore proxy appliances, see [Managing Azure Restore Proxy Appliances](restore_azure_proxy.md).

* You must set up correct time on the backup server. Otherwise you may not be able to add a Microsoft Azure Compute account or Microsoft Azure Stack Hub Compute account to Veeam Backup & Replication, or the restore process may fail.

Page updated 3/11/2025

Page content applies to build 13.0.1.1071
