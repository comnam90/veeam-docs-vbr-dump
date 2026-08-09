---
title: "Step 3. Specify Data Protection Scope"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_scope_efs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Data Protection Scope


At the Sources step of the wizard, define the scope of resources that will be available for data protection:

* Select the Account option if you want to back up EFS file systems belonging to a single AWS account. Then, specify an IAM role whose permissions will be used to access AWS services and resources, and to perform the backup operation. The role you specify must belong to an AWS account in which the resources that you want to protect reside, and must be assigned the permissions listed in section [EFS Backup IAM Role Permissions](aws_role_permissions_backup_efs.md).

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance with the Amazon EFS Backup operation selected for the role as described in section [Adding IAM Roles](aws_iam_roles_specify_permissions.md). If you have not added the necessary IAM role to the backup appliance beforehand, you can do it without closing the Add EFS Policy wizard. To do that, click Add and complete the Add IAM Role wizard.

* Select the Organization option if you want to back up EFS file systems within an AWS Organization. Then, use the Organization drop-down list to specify the source organization identity — select an entire organization or a scope of organizational units whose resources the backup appliance will back up.

For an AWS Organization or a scope of organizational units to be displayed in the list of available identities, it must be added to the backup appliance as described in section [Adding AWS Organizations](aws_organizations_add.md).

|  |
| --- |
| Important |
| If you select the Account option, it is recommended that you check whether the selected IAM role has all the permissions required to perform the operation. If some permissions of the IAM role are missing, the backup policy may fail to complete successfully. To run the IAM role permission check, click Check Permissions and follow the instructions provided in section [Checking IAM Role Permissions](aws_iam_roles_check.md#wizard). |

Excluding Items from Data Protection Scope

If you select the Organization option, you can exclude specific organizational units and AWS accounts from the data protection scope; however, keep in mind that all nested units and accounts belonging to the excluded organizational unit will also be omitted from the scope. To do that, click Choose AWS identities to exclude in the Exclusions section and do the following in Specify organization identities to exclude window:

1. Use the Type drop-down list to choose whether you want to exclude organizational units or accounts from the data protection scope.
2. Use the Name or ID drop-down list to find the necessary organizational unit or account, and then click Exclude to exclude it from the data protection scope.

For an organizational unit or account to be displayed in the list of available items, it must be part of the source organization identity, and must be included in the scope of organizational units added to the backup appliance, as described in section [Adding AWS Organizations](aws_organization_add_scope.md) (step 4).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| You can simultaneously exclude multiple items from the data protection scope — to do that, click Browse to select specific AWS identities from the global list, select check boxes next to the necessary organizational units or AWS accounts in the list of available items, and then click Exclude. If the list does not show the items that you want to exclude, click Rescan to launch the data collection process. |

[![Creating EFS Backup Policy](images/aws_efs_backup_add_iam_role.webp)](images/aws_efs_backup_add_iam_role.webp "Creating EFS Backup Policy")

Related Topics

[IAM Roles](aws_accounts_iam_roles.md)

Page updated 2026-06-15

