---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Account Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account Permissions

The account used to install Veeam Backup & Replication on a Windows-based machine must have the following permissions.

Backup Server Windows Account Permissions

| Account | Required Permission |
| Setup Account | The account used to install Veeam Backup & Replication and Veeam Plug-in for Xen must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

Xen Pool Permissions

The administrator account that the backup server uses to access the Xen pool must have the Pool Administrator role or root privileges.

Page updated 2026-07-30

