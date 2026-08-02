---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Account Permissions


To perform backup and restore operations, accounts that the plug-in uses to perform data protection and disaster recovery operations must be granted the following permissions.

Veeam Backup & Replication User Account Permissions

A user account that you plan to use when installing and working with Veeam Backup & Replication must have permissions described in section [Installing and Using Veeam Backup & Replication](required_permissions.md).

Hypervisor User Permissions

Veeam Plug-in for Universal Hypervisor API requires a user account in the hypervisor infrastructure where data protection and disaster recovery tasks will be performed.

To allow Veeam Plug-in for Universal Hypervisor API to access the Platform9 hypervisor and resources that you want to protect, the account used by Veeam Plug-in for Universal Hypervisor API must have the Administrator privileges. For more information on integration, see [Platform9 documentation](https://docs.platform9.com/private-cloud-director/integrations/veeam-integration-with-pcd/veeam-backup-and-replication).

To allow Veeam Plug-in for Universal Hypervisor API to access the VergeOS hypervosor and resources that you want to protect, the account used by Veeam Plug-in for Universal Hypervisor API must have the Administrator privileges or the following granular permissions: List/Read on the entire system, List/Read/Create/Modify/Delete on Virtual Machines, vm\_imports, files, meta\_data.

Page updated 2026-07-30

