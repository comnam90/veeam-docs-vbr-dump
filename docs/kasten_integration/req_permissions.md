---
title: "Required Permissions"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/req_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Required Permissions


Make sure the user accounts that you plan to use have permissions described in the following sections.

Veeam Backup & Replication User Account Permissions

The user account you plan to use with Kasten while connecting to Veeam Backup & Replication must have the Veeam Backup Administrator role or must be added to the user group with this role. For more information, see [Managing Users and Roles](https://helpcenter.veeam.com/docs/vbr/userguide/users_roles.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| If you work with Veeam Backup & Replication on Linux, you cannot use domain user for location profiles in Veeam Kasten. |

Veeam Backup Repositories

Make sure that either the Allow to everyone or Allow to the following accounts or groups only access permissions are granted on Veeam backup repositories where you want to keep backups exported by Veeam Kasten policies. For more information, see the [Editing Access Permissions](https://helpcenter.veeam.com/docs/vbr/userguide/access_permissions.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Do not change access permissions of repositories that already contain backups exported from Veeam Kasten, otherwise the Veeam Kasten policy will fail. |

Page updated 2026-07-09

