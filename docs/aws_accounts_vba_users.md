---
title: "Managing User Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_vba_users.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing User Accounts


The backup appliance controls access to its functionality with the help of user roles. A role defines what operations users can perform and what range of data is available to them in the backup appliance.

There are 4 user roles that you can assign to users working with the backup appliance:

* Portal Administrator — can perform all configuration actions, and can also act as a Portal Operator and Restore Operator.
* Portal Operator — can create and edit backup policies, perform backup and restore operations, manage protected data and track session statistics.
* Restore Operator — can only perform restore operations and track session statistics.
* Read-Only User — can only view backup policies, monitor protected data and track session statistics.

|  |
| --- |
| Important |
| * The list of portal users may display user accounts with the Company Administrator role assigned — these accounts are intended to be used for the integration of the backup appliance and Veeam Service Provider Console, and are created using the [Veeam Service Provider Console plug-in](https://helpcenter.veeam.com/docs/vac/provider_admin/integration_clouds.html?ver=70). It is not recommended that you perform any actions with these users. * Note that users with the Company Administrator role assigned have full access to AWS Organizations and can retrieve the organization structure. |

The following table describes the functionality available to users with different roles in the the backup appliance UI.

Managing User Accounts

| Tab | Functionality | Portal Administrator | Portal Operator | Restore Operator | Read-Only User |
| Overview | Dashboard | Full | Full | N/A | Full |
| Resources | Infrastructure | Full | Full | N/A | N/A |
| Policies | Backup policies | Full | Full | N/A | Read only |
| Backup repositories | Full | Full | N/A | Read only |
| Database accounts (RDS backup) | Full | Full | N/A | Read only |
| Protected Data | Restore | Full | Full | Full | N/A |
| Database accounts (RDS restore) | Full | Full | Full | N/A |
| File-level recovery | Full | Full | Read only | N/A |
| Remove | Full | Full | N/A | N/A |
| Sessions | Session log | Full | Full | Full | Full |
| Stop session execution | Full | Full | N/A | N/A |
| Configuration | | | | |  |
| Accounts | IAM roles, SMTP accounts, Portal Users | Full | N/A | N/A | N/A |
| Repositories | Backup repositories | Full | N/A | N/A | N/A |
| Workers | Worker instances | Full | N/A | N/A | N/A |
| Settings | General settings | Full | N/A | N/A | N/A |
| Licensing | Licensing | Full | N/A | N/A | N/A |
| Support Information | Updates and logs | Full | N/A | N/A | N/A |

In This Section

* [Adding User Accounts](aws_accounts_vba_users_create.md)
* [Editing User Account Settings](aws_accounts_vba_users_manage.md)
* [Changing User Passwords](aws_accounts_vba_users_password.md)
* [Enabling Multi-Factor Authentication](aws_accounts_vba_users_mfa.md)

Page updated 2026-05-25

