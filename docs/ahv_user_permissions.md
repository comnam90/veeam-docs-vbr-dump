---
title: "Configuring User Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_user_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring User Permissions


Veeam Backup & Replication controls access to its functionality with the help of user roles. A role defines what operations users can perform and what range of data is available to them. Veeam Backup & Replication already comes with a number of built-in default roles that allow you to perform various operations, including operations with all supported workloads. For more information, see [Managing Users and Roles](users_roles.md).

Prior to version 13.1, you had an option to create custom roles, but those roles did not include permissions required to perform operations with Nutanix AHV workloads. In version 13.1, this issue has been resolved — now you can configure custom roles to grant users granular permissions to do the following:

* Back up specific objects in Nutanix AHV clusters and Prism Centrals
* Access specific Nutanix AHV backup jobs
* Perform specific restore operations (entire VM restore, disk restore, Instant Recovery)
* Restore specific VMs using backups created by Veeam Plug-in for Nutanix AHV

* Restore objects to specific Nutanix AHV destinations

To learn how to create custom roles, see [Configuring Roles](configure_roles.md).

Related Topics

* [Configuring Backup Job Permissions Using Console](ahv_job_permissions.md)
* [Configuring Backup Job Permissions Using Web UI](ahv_job_permissions_web.md)

Page updated 2026-07-14

