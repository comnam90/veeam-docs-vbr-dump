---
title: "Managing Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repositories.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Repositories


Veeam Plug-in for Microsoft Azure uses blob containers as target locations for image-level backups of Azure VMs, backups of Azure SQL databases Cosmos DB for PostgreSQL accounts and Cosmos DB for MongoDB accounts, and backup copies of virtual network configurations. To store backups in blob containers, configure repositories. Veeam Backup for Microsoft Azure version 13 comes with 2 types of repositories:

* Backup repository — a folder created by the backup appliance in a blob container that resides in a specific Azure storage account managed by Azure users in Microsoft Azure.
* Storage vault — a folder created by Veeam Backup for Microsoft Azure in a blob container that resides in a specific Azure storage account managed by Veeam in Veeam Data Cloud Vault.

|  |
| --- |
| Important |
| A repository must not be managed by multiple backup appliances simultaneously. Retention sessions running on different appliances may corrupt backups stored in the repository, which may result in unpredictable data loss. |

In This Section

* [Adding Backup Repositories Using Console](azure_repository_add_console.md)
* [Adding Backup Repositories Using Web UI](azure_repository_add_ui.md)
* [Adding Storage Vaults Using Web UI](azure_repository_vdc_add_ui.md)
* [Editing Repository Settings](azure_repository_edit.md)
* [Rescanning Repositories](azure_repository_rescan.md)
* [Removing Repositories](azure_repository_remove.md)

Page updated 2026-07-01

