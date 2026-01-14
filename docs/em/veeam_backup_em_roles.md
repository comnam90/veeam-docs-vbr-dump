---
title: "veeam_backup_em_roles"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/veeam_backup_em_roles.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager implements security based on user roles by limiting access to features and data. This empowers the administrator to delegate permissions in a granular way, on an as-needed basis. For example, the administrator can grant permissions to another user to recover files without being able to see the content of the files.

Administrators grant users and groups access to Enterprise Manager by adding accounts. When adding an account, administrators assign a role to the account to provide it with permissions.

Enterprise Manager offers the following roles:

* Portal Administrator
* Portal User
* Restore Operator

For the Portal User and Restore Operator roles, administrators can also configure restore scope and provide permissions for guest OS file restore and application item restore.

|  |
| --- |
| Note |
| This section describes management of user accounts and roles required to work with the main Enterprise Manager UI. If you plan to provide a user with access to vSphere Self-Service Backup Portal (and not to the main Enterprise Manager UI), you do not need to configure an account for this user on the Roles tab of the Configuration view. Such accounts are configured on the Self-service tab of the Configuration view. For more information, see [Managing Tenant Accounts](em_managing_tenants.md). |

In This Section

* [Accounts and Roles Overview](em_about_accounts_and_roles.md)
* [Managing Accounts](em_managing_accounts.md)
* [Configuring Restore Scope](veeam_backup_em_restore_scope.md)
* [Configuring Permissions for File and Application Item Restore](configuring_restrictions_for_restore.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
