---
title: "Registering Application in Microsoft Identity Platform"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_register_app_azure.html"
last_updated: "8/21/2024"
product_version: "13.0.1.1071"
---

# Registering Application in Microsoft Identity Platform


To register an application in Microsoft Identity platform, do the following:

1. Sign in to Microsoft Identity platform using an account that you want to use for sending emails. The account must have an active subscription.
2. Register an application. For more information on registering applications, see [this Microsoft article](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).
3. Select API permissions and grant the application the Mail.Send permission of the Application type for the Microsoft Graph API.
4. Select Authentication > Platform configurations > Add a platform > Configure platforms > Mobile and desktop applications and specify http://localhost as a redirect URI. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app#add-a-redirect-uri).
5. Record the following data required for acquiring an access token:

* Directory (tenant) ID
* Application (client) ID


