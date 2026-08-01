---
title: "Custom Roles on Tenant Side"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_tenant_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Custom Roles on Tenant Side


The tenant can use role-based access control (RBAC) to grant users granular access to Veeam Cloud Connect backup copies. When the tenant assigns a custom role to a user or a group and includes cloud backup copies in the role restore scope, the user can see and restore only the backup copies within the assigned scope. For details on creating custom roles, see [Configuring Roles](https://helpcenter.veeam.com/docs/vbr/userguide/configure_roles.html?ver=13) in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| This capability applies only to custom roles on the tenant backup server. It is unrelated to the Veeam Backup & Replication infrastructure on the SP side, for which Veeam Cloud Connect does not support RBAC. |

Within the assigned scope, users with the custom role can perform the following operations with cloud backup copies:

* View and restore data from cloud backups and backup copies within the assigned scope.
* Perform point-in-time restore from transaction logs using the following Veeam Explorers:

* Veeam Explorer for Microsoft SQL Server
* Veeam Explorer for Oracle
* Veeam Explorer for PostgreSQL

Consider the following limitations:

* A scoped custom role sees only the cloud backup copies included in its scope. Backup copies outside the scope are hidden.
* You can create custom roles only on the tenant backup server. An SP backup server with a Veeam Cloud Connect license installed does not support role-based access control.
* Custom roles can be configured only using the backup console. They are not supported in Veeam Backup Powershell, Veeam Backup & Replication web UI or Veeam Backup Enterprise Manager REST API.
* Users with a custom role can only use credentials that another user with Admin role created.

Page updated 2026-07-29

