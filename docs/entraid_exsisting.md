---
title: "Specifying Existing Microsoft Entra Application"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entraid_exsisting.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Specifying Existing Microsoft Entra Application


This step applies only if you have selected the Use the existing account option at the [Account Type](entraid_access.md) step of the wizard.

Configuring Microsoft Entra Application

To use an existing Microsoft Entra application:

1. In the Tenant ID specify an ID of a tenant (directory) where the Microsoft Entra application resides.
2. In the Application ID field, specify the ID of the necessary application. The Microsoft Entra application must have privileges listed in section [Permissions](required_permissions.md#azure_compute).
3. In the Select authentication type area, choose whether you want to use password-based authentication (application secret) or certificate-based authentication. Then provide the necessary information.

For more information on how to get tenant and application IDs, secret and certificate, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#get-tenant-and-app-id-values-for-signing-in).

![Specifying Existing Microsoft Entra Application](images/entraid_existing.webp)


