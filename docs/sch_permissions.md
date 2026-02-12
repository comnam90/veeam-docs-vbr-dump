---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_permissions.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Account Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account Permissions

The Windows account used to install Veeam Backup & Replication on the backup server must have the following permissions.

| Account | Required Permission |
| --- | --- |
| Setup Account | The account used to install Veeam Backup & Replication and Veeam Plug-in for Scale Computing HyperCore must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

Scale Computing HyperCore Cluster Permissions

The account that the backup server uses to access the Scale Computing HyperCore cluster must have the Admin role assigned or posses the following permissions: Backup, VM Create/Edit, VM Delete, VM Power Controls, Cluster Settings.


