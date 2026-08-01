---
title: "Adding Storage Vaults Using Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_vdc_add_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Storage Vaults Using Using Console


To add a new storage vault, do the following:

1. [Launch the Add External Repository wizard](azure_repository_vdc_console_wizard.md).
2. [Specify an appliance that will manage the storage vault, and provide a name and description for the vault](azure_repository_vdc_console_appliance.md).
3. [Choose a storage vault that will be used as a target location for backups](azure_repository_vdc_console_account.md).
4. [Choose a folder in a container that will be used to store backup files](azure_repository_vdc_console_settings.md).
5. [Enable data encryption](azure_repository_vdc_console_encryption.md).
6. [Specify mount server settings](azure_repository_vdc_console_mount_server.md).
7. [Wait for the storage vault to be added to the backup infrastructure](azure_repository_vdc_console_apply.md).
8. [Finish working with the wizard](azure_repository_vdc_console_finish.md).

|  |
| --- |
| Important |
| * Before you start adding storage vaults, you must obtain [Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault_obtain_product.html) and create a Vault tenant that will be used to manage these vaults. For more information, see the Veeam Data Cloud User Guide, section [Adding Veeam Data Cloud Vault Tenants](https://helpcenter.veeam.com/docs/vdc/userguide/vault_tenants_adding_aws.html). * Veeam Plug-in for Microsoft Azure does not support adding storage vaults located in China or Azure US Government regions. |

Connecting to Existing Storage Vaults

Veeam Backup & Replication allows you to connect to existing storage vaults that already contain image-level backups created by the backup appliance. You can then use the Veeam Backup & Replication console to copy and import these backups and restore Azure VMs from them. For more information on usage scenarios, see [External Repositories](external_repository.md).

To connect to a storage vault, do the following:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to External Repositories and click Connect to Repository on the ribbon.

Alternatively, you can right-click the External Repositories node and select Connect to.

1. Complete the New External Repository wizard as described in section [Adding External Veeam Data Cloud Vault Storage](external_repositories_add.md).

Page updated 2026-07-28

