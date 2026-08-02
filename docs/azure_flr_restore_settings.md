---
title: "Step 3. Configure Restore Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_flr_restore_settings.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 3. Configure Restore Settings


At the Restore Settings step of the wizard, choose whether you want to restore files to the original location. To do that, set the Restore to original location toggle to On and click the link in the Service account field. Then, select a service account that will be used for the restore operation. The specified service account must be assigned permissions listed in section [Azure VM Permissions](azure_vm_permissions.md#restore).

For a service account to be displayed in the list of available accounts, it must be added to Veeam Backup for Microsoft Azure and assigned the Azure VMs Restore operational role as described in section [Adding Service Accounts](azure_service_account_add.md); also, it must belong to the Microsoft Entra tenant and Azure subscription that contain the Azure VM whose files will be restored. If you have not added the necessary account to Veeam Backup for Microsoft Azure beforehand, you can do it without closing the File-Level Recovery wizard. To do that, click Add and complete the Add Account wizard.

[![File-Level Recovery Restore Settings](images/azure_flr_original_location.webp)](images/azure_flr_original_location.webp "File-Level Recovery Restore Settings")

Page updated 2025-04-07

