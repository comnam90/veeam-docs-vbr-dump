---
title: "Step 4. Connect to Microsoft Azure"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_tenant_restore_logon.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Step 4. Connect to Microsoft Azure


At the Logon step of the wizard, do the following:

1. Copy the authentication code to the clipboard.

1. Open the https://microsoft.com/devicelogin link.
2. On the Microsoft Azure device authentication page, do the following:

1. Paste the code that you have copied and click Next.

1. Specify the name of a Microsoft Entra ID user account associated with the tenant whose data you want to restore. The name of the account must be specified in the username@domain format.

Keep in mind that the account must have all the permissions required to perform operations with the selected items. For more information on the required permissions, see [Permissions](entra_id_permissions.md#restore).

1. Wait for the authentication process to complete, check whether any errors occurred, and then close the Microsoft Azure device authentication page.

1. Back to the Microsoft Entra ID Tenant Restore wizard, click Next.

[![Log on to Microsoft](images/entra_id_restore_prop_logon.webp)](images/entra_id_restore_prop_logon.webp "Log on to Microsoft")


