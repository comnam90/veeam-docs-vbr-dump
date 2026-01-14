---
title: "Step 3. Select Authentication Method"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_select_authentication_method_doc_m365.html"
last_updated: "8/22/2024"
product_version: "13.0.1.1071"
---

# Step 3. Select Authentication Method

In this article

At this step of the wizard, select either modern or basic authentication and specify authentication settings.

Modern Authentication

To use modern authentication, do the following:

1. From the Authentication method drop-down list, select Modern authentication.

This will allow Veeam Backup for Microsoft 365 to use a Microsoft Entra application for data restore. Such an application is used to restore the specified object back to Microsoft 365 organizations with enabled multi-factor authentication (MFA). For more information, see the [Adding Microsoft 365 Organizations](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_add_office365_org.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide.

1. From the Region drop-down list, select a region to which your target SharePoint Online organization belongs.
2. In the Organization name field, enter a name of your target SharePoint Online organization.
3. In the Application ID field, enter an identification number of the Microsoft Entra application that you want to use for data restore.

By default, Veeam Explorer for Microsoft SharePoint populates this field with the identification number of the application that was used during a backup session. If you want to use another application, make sure to grant this application required permissions. For more information, see the [Microsoft Entra Application Permissions](https://helpcenter.veeam.com/docs/vbo365/guide/azure_ad_applications.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide.

[![Select Authentication Method](images/select_authentication_method_2.webp)](images/select_authentication_method_2.webp "Select Authentication Method")

Basic Authentication

To use basic authentication, do the following:

1. From the Authentication method drop-down list, select Basic authentication.
2. From the Region drop-down list, select a region to which your target SharePoint Online organization belongs.
3. In the Username and Password fields, enter credentials to connect to the SharePoint organization.

[![Select Authentication Method](images/select_authentication_method_basic_2.webp)](images/select_authentication_method_basic_2.webp "Select Authentication Method")

Page updated 8/22/2024

Page content applies to build 13.0.1.1071
