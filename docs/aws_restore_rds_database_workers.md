---
title: "Step 3. Specify Account Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_database_workers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Account Settings


At the Account step of the wizard, choose whether you want to use an IAM role of a standalone AWS account or an AWS account of an AWS Organization to allow the backup appliance to perform the restore operation. For information on the permissions that the IAM role must have to perform the restore operation, see [RDS Database Restore IAM Permissions](aws_role_permissions_restore_db.md).

Depending on whether the AWS account to which the source DB instances belong is a part of an AWS Organization, the backup appliance automatically does either of the following:

* If the AWS account is a part of an AWS Organization,the backup appliance chooses the AWS account itself and the organization identity that contains the account — in this case, the Organization account option is selected by default.
* If the AWS account is not a part of an AWS Organization, the backup appliance chooses an IAM role from the AWS account — in this case, the IAM Role option is selected by default.

|  |
| --- |
| Important |
| For the backup appliance to be able to perform the restore operation, you must also specify an IAM that will be attached to the worker instances and used by the backup appliance to communicate with these instances. For more information, see [Configuring Worker Settings](aws_restore_rds_database_account_2.md). |

Specifying IAM Role from Single AWS Account

To specify an IAM role to be used for the restore operation, select the IAM role option and choose the necessary IAM role from the list. Keep in mind that the selected role must belong to an AWS account to which you plan to restore RDS resources.

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance with the Amazon RDS Restore operation selected as described in section [Adding IAM Roles](aws_iam_roles_add.md). If you have not added the necessary IAM role to the backup appliance beforehand, you can do it without closing the RDS Database Restore wizard. To do that, click Add and complete the Add IAM Role wizard.

|  |
| --- |
| Important |
| It is recommended that you check whether the selected IAM role has all the permissions required to perform the operation. If some permissions of the IAM role are missing, the restore operation may fail to complete successfully. To run the IAM role permission check, click Check Permissions and follow the instructions provided in section [Checking IAM Role Permissions](aws_iam_roles_check.md#wizard). |

Specifying AWS Account Within AWS Organization

To specify an AWS account to be used for the restore operation, select theOrganization accountoption and do the following:

1. From the Organization drop-down list, choose the necessary organization identity — either an entire AWS Organization or a limited scope of organizational units.

For an organization or a scope of organizational units to be displayed in the list of available identities, it must be added to the backup appliance as described in section [Managing AWS Organizations](aws_managing_organizations.md).

1. From the Account drop-down list, choose an account that contains the IAM role whose permissions will be used to perform the restore operation. The role must be specified in the settings of the selected organization identity, as described in section [Adding AWS Organizations](aws_organization_add_settings.md#backup_role) (step 3).

For an AWS account to be displayed in the list of available accounts, it must be included in the the selected organization identity.

[![Restoring RDS Databases](images/aws_database_restore_account.webp)](images/aws_database_restore_account.webp "Restoring RDS Databases")

Page updated 2026-05-22

