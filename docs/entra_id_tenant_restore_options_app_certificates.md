---
title: "Adding Application Certificates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_tenant_restore_options_app_certificates.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Application Certificates


[This step applies only if you have chosen to restore applications when proceeding with the wizard]

When processing an application added to the restore scope, Veeam Backup for Microsoft Entra ID does not recover its certificates. For the restored application to be able to authenticate in Microsoft Entra ID, at least one certificate must be manually uploaded for this application — to do that, click Add Application Certificates and browse to the necessary certificate file on the local machine. If you have not downloaded the application certificate beforehand, you can create a new certificate as described in [Microsoft Docs](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=certificate).

[![Configure Restore Options](images/entra_id_restore_user_options.webp)](images/entra_id_restore_user_options.webp "Configure Restore Options")

Page updated 2026-07-14

