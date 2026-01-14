---
title: "req_permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/req_permissions.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---


In this article

Make sure the user accounts that you plan to use have permissions described in the following sections.

Veeam Backup & Replication User Account Permissions

The user account you plan to use with Kasten while connecting to Veeam Backup & Replication must have the Veeam Backup Administrator role or must be added to the user group with this role. For more information, see [Managing Users and Roles](https://helpcenter.veeam.com/docs/backup/vsphere/users_roles.html?ver=120) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| If you work with Veeam Backup & Replication on Linux, you cannot use domain user for location profiles in Veeam Kasten. |

Veeam Backup Repositories

Make sure that either the Allow to everyone or Allow to the following accounts or groups only access permissions are granted on Veeam backup repositories where you want to keep backups exported by Veeam Kasten policies. For more information, see the [Access Permissions (Step 4)](https://helpcenter.veeam.com/docs/backup/vsphere/access_permissions.html?ver=120) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Do not change access permissions of repositories that already contain backup exported from Veeam Kasten, otherwise the Veeam Kasten policy will fail. |

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
