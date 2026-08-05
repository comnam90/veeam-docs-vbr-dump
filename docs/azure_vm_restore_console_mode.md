---
title: "Step 3. Choose Restore Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_restore_console_mode.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 3. Choose Restore Mode


At the Restore Mode step of the wizard, do the following:

1. Choose whether you want to restore the selected Azure VM to the original or to a new location.

1. Click Pick account to use to select a service account whose permissions will be used to perform the restore operation. For more information on the required permissions, see [Service Account Permissions](azure_service_account_permissions.md).

For a service account to be displayed in the list of available accounts, it must be added to Veeam Backup for Microsoft Azure and assigned the Azure VM Restore operational role as described in section [Adding Service Accounts](azure_service_account_select_roles.md).

|  |
| --- |
| Note |
| To perform restore operations, Veeam Backup & Replication uses permissions of service accounts that belong to the tenants that contained original VMs. If none of the service accounts added to Veeam Backup for Microsoft Azure belong to these tenants, the Restore to the original location option will not be available. |

[![Restore to Microsoft Azure - Mode](images/azure_restore_from_snapshot_restore_mode.webp)](images/azure_restore_from_snapshot_restore_mode.webp "Restore to Microsoft Azure - Mode")

Page updated 2025-08-26

