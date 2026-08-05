---
title: "Configuring Backup Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_target_settings_backups_fsx.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Backup Settings


To specify backup vaults used to store backups of the selected FSx file systems, do the following:

1. In the Backups section of the Targets step of the wizard, click Choose backup vaults.
2. In the Choose backup vaults window, for each AWS Region included in the policy, specify a backup vault to save and organize file system backups. To do that:

1. Select an AWS Region and click Edit.
2. [Applies only if you have chosen the Account option at the Sources step of the wizard] In the Edit Backup Vault window, from the Backup vault drop-down list, select the necessary backup vault.

For a backup vault to be displayed in the list of available backup vaults, it must be created in the AWS Backup console as described in [AWS Documentation](https://docs.aws.amazon.com/aws-backup/latest/devguide/create-a-vault.html#creating-a-vault-console). If no custom backup vaults exist in the selected AWS Region, the list will contain the default backup vault only.

1. [Applies only if you have chosen the Organization option at the Sources step of the wizard] In the Edit Backup Vault window, in the Tag key and Tag value fields, specify a key and value of the AWS tag associated with the necessary backup vaults. The backup vault with the specified tag must be created in each AWS account within the AWS Organization or organizational units added to the backup policy. Note that the specified tag must not be associated with multiple backup vaults in the same AWS Region and account within the organization.

To configure mapping for all AWS Regions within the selected organization at once, click Set Mapping for All Regions.

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS does not support storing backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.  * Make sure that the type of file system added to the backup scope is supported by the AWS Backup service in the source AWS Region. Otherwise, the backup operation will fail to complete successfully. For the list of supported AWS Regions, see [AWS Documentation](https://docs.aws.amazon.com/aws-backup/latest/devguide/backup-feature-availability.html#supported-services-by-region). * Make sure policies assigned to the selected backup vault allow the backup appliance to access vault resources and to perform backup, backup copy and restore operations. For more information on vault access policies, see [AWS Documentation](https://docs.aws.amazon.com/aws-backup/latest/devguide/create-a-vault-access-policy.html).  * For the backup appliance to be able to back up FSx file systems, you must enable the Opt-in service for the FSx resource type in the AWS Backup settings. Otherwise, the backup appliance will automatically enable the service for each AWS Region specified in the Backups section in your AWS account while performing backup operations. |

1. Click Save.

1. To save changes made to the backup policy settings, click Apply.

[![Creating FSx Backup Policy](images/aws_backup_add_backup_settings_fsx.webp)](images/aws_backup_add_backup_settings_fsx.webp "Creating FSx Backup Policy")

Page updated 2026-05-21

