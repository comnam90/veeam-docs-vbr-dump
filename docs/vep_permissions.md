---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

The following table lists the user account permissions necessary to launch Veeam Explorer for PostgreSQL and recover PostgreSQL data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for PostgreSQL launch | The account used to run Veeam Explorer for PostgreSQL must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for PostgreSQL is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for PostgreSQL restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore, Publish, Instant Recovery | The account used for PostgreSQL data recovery must be a Linux user with root privileges on the target machine. Root privileges are required to mount the backed-up file system to the target server and to communicate with PostgreSQL. |
| Export | The account used to connect to the staging server must be a Linux user with root privileges.  Consider the following when configuring the account used to connect to the target server:   * [For Windows-based backup servers] When you export data to the local host where Veeam Explorer for PostgreSQL is running, the account under which Veeam Explorer for PostgreSQL is running must be a member of the local Administrators group. * When you export data to a Linux server, the account used to connect to the target server can be a Linux user with non-root privileges. |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
