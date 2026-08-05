---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_overview.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Overview


Veeam Backup for Microsoft Azure is a solution developed for protection and disaster recovery tasks for Microsoft Azure environments: Azure VMs, Azure SQL databases, Cosmos DB accounts and Azure Files. Veeam Backup for Microsoft Azure also allows you to back up and restore Azure Virtual Network configurations.

With Veeam Backup for Microsoft Azure, you can perform the following data protection and disaster recovery operations:

* Create image-level backups and cloud-native snapshots of Azure VMs.
* Create backups of Azure SQL databases.
* [Available only for backup appliances managed by Veeam Backup & Replication] Create backups of Cosmos DB accounts.
* Create cloud-native snapshots of Azure file shares.

* [Available only for backup appliances managed by Veeam Backup & Replication] Create backups of virtual network configurations.
* Create backups of the Veeam Backup for Microsoft Azure configuration database.

To recover backed-up data, you can perform the following operations:

* Restore entire Azure VMs, individual virtual disks, and guest OS files and folders.
* Restore Azure SQL databases.
* [Available only for backup appliances managed by Veeam Backup & Replication] Restore Cosmos DB accounts.
* [Available only for backup appliances managed by Veeam Backup & Replication] Restore entire virtual network configurations of Azure subscriptions.
* [Available only for backup appliances managed by Veeam Backup & Replication] Restore specific items of virtual network configurations of Azure subscriptions.

* Restore individual files of Azure VMs.
* Restore individual files of Azure file shares.

* [Available only for backup appliances managed by Veeam Backup & Replication] Restore entire Azure VMs to AWS, Google Cloud and Nutanix AHV.
* [Available only for backup appliances managed by Veeam Backup & Replication] Perform Instant Recovery of Azure VMs to VMware vSphere and Hyper-V environments, and to Nutanix AHV clusters.

* Restore the Veeam Backup for Microsoft Azure configuration database to the same or another backup appliance.

|  |
| --- |
| Important |
| Starting from Veeam Backup for Microsoft Azure version 6.0, Veeam Backup for Microsoft Azure is part of the Veeam Backup & Replication solution, and some features are available only for backup appliances managed by Veeam Backup & Replication. For more information, see [Integration with Veeam Backup & Replication](azure_integration_vbr.md). |

Page updated 2025-10-21

