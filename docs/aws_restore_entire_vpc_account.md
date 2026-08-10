---
title: "Step 3. Specify Account Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_vpc_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Account Settings


At the Account step of the wizard, choose whether you want to use an IAM role of a standalone AWS account, an AWS account of an AWS Organization, or one-time access keys of an IAM user to allow the backup appliance to perform the restore operation. For information on the permissions that the IAM role or IAM user must have to perform the restore operation, see [VPC Configuration Restore IAM Permissions](aws_role_permissions_restore_vpc.md).

|  |
| --- |
| Note |
| Depending on whether the AWS account to which the source VPC configuration belongs is a part of an AWS Organization, the backup appliance automatically does either of the following:   * If the AWS account is a part of an AWS Organization, the backup appliance chooses the AWS account itself and the organization identity that contains the account — in this case, the Organization account option is selected by default. * If the AWS account is not a part of an AWS Organization, the backup appliance chooses an IAM role from the AWS account — in this case, the IAM Role option is selected by default. |

Specifying IAM Role of Standalone AWS Account

To specify an IAM role to be used for the restore operation, select the IAM role option and choose the necessary IAM role from the list. The selected IAM role must belong to an AWS account in which you plan to restore the VPC configuration.

For an IAM role to be displayed in the IAM role list, it must be added to the backup appliance with the Amazon VPC Restore operationselected as described in section [Adding IAM Roles](aws_iam_roles_add.md). If you have not added the necessary IAM role to the backup appliance beforehand, you can do it without closing the VPC Restore wizard. To do that, click Add and complete the Add IAM Role wizard.

|  |
| --- |
| Important |
| It is recommended that you check whether the selected IAM role has all the permissions required to perform the operation. If some permissions of the IAM role are missing, the restore operation may fail to complete successfully. To run the IAM role permission check, click Check Permissions and follow the instructions provided in section [Checking IAM Role Permissions](aws_iam_roles_check.md#wizard). |

Specifying AWS Account of AWS Organization

To specify an AWS account to be used for the restore operation, select theOrganization accountoption and do the following:

1. From the Organization drop-down list, choose the necessary organization identity — either an entire AWS Organization or a limited scope of organizational units.

For an organization or a scope of organizational units to be displayed in the list of available identities, it must be added to the backup appliance as described in section [Managing AWS Organizations](aws_managing_organizations.md).

1. From the Account drop-down list, choose an account that contains the IAM role whose permissions will be used to perform the restore operation. The role must be specified in the settings of the selected organization identity, as described in section [Adding AWS Organizations](aws_organization_add_settings.md#backup_role) (step 3).

For an AWS account to be displayed in the list of available accounts, it must be created in the the selected organization identity as described in [AWS Documentation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts_create.html).

Specifying One-Time Access Keys of IAM User

To specify one-time access keys for restore, select the Temporary access keys option and use the Access key and Secret key fields to provide the [access keys of an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html). Note that the IAM user must belong to an AWS account in which you plan to restore the VPC configuration.

|  |
| --- |
| Note |
| The backup appliance does not store one-time access keys in the configuration database. |

[![Restoring VPC Configuration](images/aws_restore_account_vpc.webp)](images/aws_restore_account_vpc.webp "Restoring VPC Configuration")

Page updated 2026-05-22

