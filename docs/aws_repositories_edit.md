---
title: "Editing Repository Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repositories_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Repository Settings


The settings that you can modify for a repository depend on whether the repository has been added to the backup infrastructure using the Veeam Backup & Replication console or the the backup appliance Web UI.

Editing Storage Vault Settings Using Veeam Backup & Replication Console

For each storage vault, you can modify settings configured while adding the vault to the backup infrastructure:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to External Repositories.
3. Select the necessary storage vault and click Edit Repository on the ribbon.

Alternatively, you can right-click the storage vault and select Properties.

1. Complete the Edit External Repository wizard:

1. To specify a new name and description for the storage vault, follow the instructions provided in section [Adding Storage Vaults Using Console](aws_add_vault_appliance.md) (step 2).
2. To register a backup server in Veeam Data Cloud Vault, assign the storage vault to the backup server, or change the gateway server used to access the repository, follow the instructions provided in section [Adding Storage Vaults Using Console](aws_add_vault_account.md) (step 3).
3. To change the encryption settings of the storage vault, follow the instructions provided in section [Adding Storage Vaults Using Console](aws_add_vault_encryption.md) (step 5).
4. To change the settings for the mount servers that will be used for Instant Recovery, guest OS file restore and application item restore, follow the instructions provided in [Adding Storage Vaults Using Console](aws_add_vault_mount_server.md) (step 6).
5. At the Apply step of the wizard, wait for the changes to be applied and click Next.
6. At the Summary step of the wizard, review summary information and click Finish to confirm the changes.

Editing Backup Repository Settings Using Veeam Backup & Replication Console

For each standard backup repository, you can modify settings configured while adding the repository to the backup infrastructure:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to External Repositories.
3. Select the necessary repository and click Edit Repository on the ribbon.

Alternatively, you can right-click the repository and select Properties.

1. Complete the Edit External Repository wizard:

1. To specify a new name and description for the repository, follow the instructions provided in section [Creating New Repositories](aws_add_s3_appliance.md) (step 2).
2. To change the access keys of the IAM user and the gateway server used to access the repository, follow the instructions provided in section [Creating New Repositories](aws_add_s3_account.md) (step 3).
3. To enable encryption or change the encryption settings of the repository, follow the instructions provided in section [Creating New Repositories](aws_add_s3_encryption.md) (step 6).

|  |
| --- |
| Important |
| If you change the encryption settings of the repository from the Veeam Backup & Replication console, Veeam Backup & Replication will not propagate these settings to the backup appliance automatically. Consider updating the settings manually as described in [Editing Backup Repository Settings Using Backup Appliance Web UI](#editing_repo_settings). |

1. To change the settings for the mount servers that will be used for Instant Recovery, guest OS file restore and application item restore, follow the instructions provided in section [Creating New Repositories](aws_add_s3_mount_server.md) (step 7).
2. To specify the S3 interface endpoint that will be used to communicate with the Amazon S3 service in private deployment mode, follow the instructions provided in section [Creating New Repositories](aws_add_s3_s3endpoint.md) (step 8).
3. At the Apply step of the wizard, wait for the changes to be applied and click Next.
4. At the Summary step of the wizard, review summary information and click Finish to confirm the changes.

[![Edit Repository](images/aws_editing_repository.webp)](images/aws_editing_repository.webp "Edit Repository")

Editing Backup Repository Settings Using Backup Appliance Web UI

For each backup repository, you can modify settings configured while adding the repository to the backup appliance:

1. Switch to the Configuration page.

1. Navigate to Repositories.

1. Select the backup repository and click Edit.

1. Complete the Edit Repository wizard.

1. To provide a new name and description for the backup repository, follow the instructions provided in section [Adding Backup Repositories Using Web UI](aws_repository_add_name.md) (step 2).
2. To change the IAM role whose permissions the backup appliance uses to access the repository, follow the instructions provided in section [Adding Backup Repositories Using Web UI](aws_repository_add_folder.md#Role) (step 3).
3. [Applies only to repositories managed by another backup appliance] To change the owner of the backup repository, navigate to the Bucket step and click Next. Then, follow the instructions provided in section [Adding Backup Repositories Using Web UI](aws_repository_owner.md) (step 3).
4. To enable data encryption or change the configured encryption settings, follow the instructions provided in section [Adding Backup Repositories Using Web UI](aws_repositories_add_encryption.md) (step 4).
5. To specify the S3 interface endpoint that will be used to communicate with the Amazon S3 service in private deployment mode, follow the instructions provided in section [Adding Backup Repositories Using Web UI](aws_repositories_add_s3endpoint.md) (step 5).
6. At the Summary step of the wizard, review summary information, choose whether you want to proceed to the [Session Log page](aws_reporting.md#ui) to track the progress of modifying the backup repository settings, and click Finish to confirm the changes.

|  |
| --- |
| Important |
| After you add storage vaults to the backup infrastructure using the Veeam Backup & Replication console, the Repositories page will also display these vaults — but you will not be able to modify the vault settings from the backup appliance Web UI. To modify the vault settings, follow the instructions provided in section [Editing Repository Settings](#editing_repo_settings_console). |

[![Editing Repository Settings](images/aws_repo_edit.webp)](images/aws_repo_edit.webp "Editing Repository Settings")

Page updated 2026-06-22

