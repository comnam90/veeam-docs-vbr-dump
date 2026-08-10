---
title: "Private Network Deployment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_private_network_deployment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Private Network Deployment


The private deployment feature allows you to increase the security of your environment by retaining network traffic within a private network.

With Veeam Plug-in for Microsoft Azure, you can perform the following operations in a private environment:

* [Create image-level backups and cloud-native snapshots of Azure VMs](azure_vm_backup_pne.md).
* [Create backups of Azure SQL databases](azure_sql_backup_pne.md).
* [Create backups of Cosmos DB accounts](azure_cosmos_backup_pne.md).
* [Create cloud-native snapshots of Azure file shares](azure_fs_backup_pne.md).

When a backup appliance is deployed in a private environment, it is not assigned any public IPv4 address, and you will have to perform a number of additional configuration actions to allow private network access. For more information, see [Working in Private Environments](azure_app_private_network.md).

Page updated 2026-07-01

