---
title: "Registering Application in Microsoft Azure Portal"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/registering_azure_app.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Registering Application in Microsoft Azure Portal


Before the Veeam Backup Enterprise Manager web application can obtain an access token, you need to register the application with the Microsoft identity platform. Upon registration you will obtain application essentials that are required for acquiring an access token.

You can register Veeam Backup Enterprise Manager in the Microsoft Azure portal. For more information on registering applications, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

1. Log in to the Microsoft Azure portal under an account that you want to use for sending email notifications. The account must have an active subscription and the permissions to register Microsoft Entra applications.
2. Create a new app registration for Veeam Backup Enterprise Manager:

1. In the Name field, specify a display name for your application.
2. In the Supported account types section, select the Accounts in this organizational directory only option.
3. In the Redirect URI section, select the Web option from the platform list and specify the following URI:

|  |
| --- |
| https://<EnterpriseManagerServer>/api/Notifications/GrantPermissions |

where <EnterpriseManagerServer> is a host name or IP address of the host where the Enterprise Manager server resides.

1. Grant the application the Mail.Send permission of Microsoft Graph. This will allow Veeam Backup Enterprise Manager to call the Microsoft Graph API for sending email notifications.
2. Add a new client secret. It is used to prove the application identity to the Microsoft identity platform.
3. Record the following data required for acquiring an access token:

* Directory (tenant) ID
* Application (client) ID
* Client secret value


