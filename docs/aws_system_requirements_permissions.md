---
title: "IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_system_requirements_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# IAM Permissions


To perform data protection and disaster recovery operations, you must specify IAM roles whose permissions backup appliances will use to access AWS services and resources.

When you deploy a backup appliance, the [Default Backup Restore IAM role](aws_deploying_appliances.md) is automatically created and added to the appliance. This IAM role is assigned all permissions required to perform operations in the same AWS account where the backup appliance resides. However, you can manually create additional IAM roles with granular permissions to perform specific operations in this or in other AWS accounts [using the AWS Management Console](aws_create_iam_policy_role.md), and then add them to the backup appliance.

For more information on IAM roles, see [Managing IAM Roles](aws_accounts_iam_roles.md).

In This Section

* [Organization Rescan IAM Permissions](aws_organization_permissions.md)
* [Worker IAM Permissions](aws_role_permissions_service.md)
* [Repository IAM Permissions](aws_role_permissions_repo.md)
* [Backup IAM Permissions](aws_role_permissions_backup.md)
* [Restore IAM Permissions](aws_role_permissions_restore.md)
* [Full List of IAM Permissions](aws_full_list_permissions.md)
* [IAM Permissions Changelog](aws_permissions_changelog.md)

Page updated 2026-07-24

