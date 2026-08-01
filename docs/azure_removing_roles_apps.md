---
title: "Removing IAM Roles and Microsoft Entra Applications"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_roles_apps.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Removing IAM Roles and Microsoft Entra Applications


|  |
| --- |
| Important |
| Do not remove IAM roles and Microsoft Entra applications if they are still used by other backup appliances. |

To remove IAM roles and Microsoft Entra applications created by Veeam Backup for Microsoft Azure, do the following:

1. Sign in to the Microsoft Azure portal using credentials of the Microsoft Azure account that you used to install Veeam Backup for Microsoft Azure.

1. Navigate to Microsoft Entra ID > App registrations.

1. On the All applications tab, click Start typing a display name or application (client) ID and enter an application ID in the search field.

|  |
| --- |
| Tip |
| If you do not know the ID of an Microsoft Entra application created by Veeam Backup for Microsoft Azure, navigate to Accounts, switch to the Service Accounts tab, select the necessary account and click Edit. At the account type step of the opened wizard, select the Specify existing account option and click Next. Then, navigate to the Application ID field and copy the ID to the clipboard. |

1. On the application page, click Delete.

In the Delete app registration window, click Delete to confirm the action.

1. Navigate to Subscriptions and click the subscription that manages costs of the backup appliance.

On the subscription page, do the following:

1. Navigate to Access control (IAM) > Roles.
2. Select check boxes next to each Veeam Service Account role you want to remove and click Remove.

Page updated 2024-08-26

