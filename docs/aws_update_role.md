---
title: "Updating IAM Roles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_update_role.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Updating IAM Roles


When you update the backup appliance to a newer version, the improvements and new features instantly become available in the appliance. However, to meet new requirements, IAM roles must be assigned missing permissions manually either using the backup appliance Web UI or the AWS Management Console.

To update the IAM role, run a permission check for this role at the IAM Roles tab as described in section [Checking IAM Role Permissions](aws_iam_roles_check.md#check_permissions_iam_role_tab). The permission check verifies whether the IAM role has all the permissions required to perform operations with the workloads selected at the Permissions step of the Add IAM Role wizard. You can track the progress and view the results of the permission check in the AWS Permission Check window. If some of the IAM role permissions are missing, the check will complete with errors, and the Missing Permissions column will display the list of permissions that must be granted to the IAM role. You can grant the missing permissions to the IAM role using the AWS Management Console or [instruct the backup appliance to do it](aws_iam_roles_check.md). To learn how to grant permissions to IAM roles using the AWS Management Console, see [Appendix B. Creating IAM Policies in AWS](aws_create_iam_policy.md).

|  |
| --- |
| Note |
| The [Default Backup Restore IAM role](aws_deploying_appliances.md) is updated automatically during the upgrade of backup appliances from the Veeam Backup & Replication console. For more information, see [Updating Appliances Using Console](aws_upgrade_appliance_console.md#default_role). |

Page updated 2026-05-20

