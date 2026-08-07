---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Permissions


The following table lists the user account permissions necessary to launch Veeam Explorer for PostgreSQL and recover PostgreSQL data.

Permissions

| Operation | Required Roles and Permissions |
| Veeam Explorer for PostgreSQL launch | The account used to run Veeam Explorer for PostgreSQL must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for PostgreSQL is running.  * The account must have one of the following roles on the backup server:  * The Backup Administrator or Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for PostgreSQL restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore, Publish, Instant Recovery of PostgreSQL Instances | When restoring to a Windows machine, make sure that the user account is member of the local Administrators group.  When restoring to a Linux machine, make sure that the user account is a Linux user with root privileges on the target machine. Root privileges are required to mount the backed-up file system to the target server and to communicate with PostgreSQL. |
| Restore of PostgreSQL Databases | When you restore individual databases, Veeam Explorer for PostgreSQL connects to the PostgreSQL instance on the target Linux machine to restore the selected databases. In addition to the account requirements for instance restore, you must specify a PostgreSQL account to authenticate to the target instance. You can use one of the following options:   * The credentials of the Linux system user. * A system user with peer authentication (no password required). * A database user account and its password.   The account must have superuser privileges on the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html). |
| Export of PostgreSQL Databases | Consider the following when configuring the account used to connect to the staging server:   * When exporing data from a backup of a Windows machine, the account used to connect to the staging server must be a member of the local Administrators group. * When exporing data from a backup of a Linux machine, the account used to connect to the staging server must be a Linux user with root privileges.   Consider the following when configuring the account used to connect to the target server:   * [For Windows-based backup servers] When you export data to a Windows machine, the account used to connect to the target server must be a member of the local Administrators group. * When you export data to a Linux server, the account used to connect to the target server can be a Linux user with non-root privileges. |

Page updated 2026-07-29

