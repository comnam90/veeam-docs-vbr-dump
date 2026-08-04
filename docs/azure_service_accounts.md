---
title: "Managing Service Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_service_accounts.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Service Accounts


For each data protection and disaster recovery operation performed for an Azure resource, you must specify a service account that has access to the resource and a set of permissions that determine what operations are allowed for the resource.

Particularly, the backup appliance uses service accounts to perform the following tasks:

* To enumerate resources added to backup policies.

* To create snapshots and backups of Azure resources protected by policies.
* To create and manage worker instances.
* To create and manage backup repositories.
* To attach virtual disks to worker instances when performing image-level backup.
* To restore Azure VMs, virtual disks, and files and folders from cloud-native snapshots and image-level backups.
* To restore Azure SQL databases and Cosmos DB accounts from backups.
* To restore files of Azure file shares from cloud-native snapshots.
* To create backups of Azure virtual network configurations.
* To restore backups of Azure virtual network configurations from backups.

In This Section

* [Adding Service Accounts](azure_service_account_add.md)
* [Editing Service Accounts](azure_service_account_edit.md)
* [Checking Service Account Permissions](azure_service_account_check.md)
* [Removing Service Accounts](azure_service_account_remove.md)

Page updated 2026-07-01

