---
title: "Managing IAM Roles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_iam_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing IAM Roles


|  |
| --- |
| Note |
| This section assumes that you have a good understanding of [IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html), [IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) and [IAM Identity Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html). |

Backup appliance use permissions of IAM roles to access AWS services and resources, and to perform the backup and restore operations. For example, backup appliances may require access to the following AWS resources:

* EC2 resources — to display the list of EC2 instances in backup policy settings, to create cloud-native snapshots, snapshot replicas, to deploy worker instances and to restore backed-up data.
* S3 resources — to store backed-up data in backup repositories, to perform transform operations with backup chains, and to copy backed-up data from backup repositories to worker instances during restore.

For each data protection and disaster recovery operation performed by the backup appliance, you must specify an IAM role. By design, backup appliances come with the Default Backup Restore IAM role. This role is added to the appliance configuration database upon product installation and is automatically assigned all the permissions required to perform data protection tasks within the initial AWS account in which the backup appliance resides.

If you want to back up and restore resources in other AWS accounts, or if you want to specify custom IAM roles with granular permissions to perform specific operations, [add IAM roles to the backup appliance](aws_iam_roles_add.md). You can add IAM roles that already exist in your AWS accounts, or instruct the backup appliance to automatically create IAM roles with predefined permission sets in AWS — and then add these roles to the backup appliance.

To help you configure the necessary IAM roles in AWS and grant all the required permissions, the backup appliance allows you to [create IAM role templates](aws_iam_template_add.md). Alternatively, you can create IAM roles in the AWS Management Console as described in [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

In This Section

* [Adding IAM Roles](aws_iam_roles_add.md)
* [Editing IAM Role Settings](aws_iam_roles_edit.md)
* [Checking IAM Role Permissions](aws_iam_roles_check.md)
* [Removing IAM Roles](aws_iam_roles_remove.md)

Page updated 2026-05-21

