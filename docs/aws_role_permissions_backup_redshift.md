---
title: "Redshift Cluster Backup IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Cluster Backup IAM Role Permissions


Backup appliances use Redshift Backup IAM roles to perform the following operations:

* To enumerate resources added to a backup policy.
* To create backups of Redshift clusters.

To perform these operations, IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [Redshift backup policy settings](aws_add_policy_scope_redshift.md#account) must meet the following requirements:

1. Backup appliances must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).
2. The AWS Backup service must be granted permissions to assume the IAM roles.

To allow the AWS Backup service to assume an IAM role, configure trust relationships for the role and add the following statement to the trust policy:

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": "sts:AssumeRole",       "Principal": {         "Service": "backup.amazonaws.com"       }     }   ]  } |

To learn how to modify role trust policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/roles-managingrole-editing-console.html#roles-managingrole_edit-trust-policy).

1. The IAM roles must be granted the following permissions:

* IAM roles specified in the [backup policy settings](aws_add_policy_scope_redshift.md#role):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup:DeleteRecoveryPoint",                 "backup:DescribeBackupJob",                 "backup:DescribeRegionSettings",                 "backup:DescribeRecoveryPoint",                 "backup:ListBackupVaults",                 "backup:ListRecoveryPointsByBackupVault",                 "backup:ListTags",                 "backup:StartBackupJob",                 "backup:StopBackupJob",                 "backup:UpdateRegionSettings",                 "ec2:DescribeRegions",                 "ec2:DescribeAvailabilityZones",                 "events:DeleteRule",                 "events:DescribeRule",                 "events:ListTargetsByRule",                 "events:PutRule",                 "events:PutTargets",                 "events:RemoveTargets",                 "iam:GetRole",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "iam:ListAccountAliases",                 "redshift:DescribeClusters",                 "redshift:CreateTags",                 "redshift:DescribeTags",                 "redshift:DeleteTags",                 "redshift:CreateClusterSnapshot",                 "redshift:DeleteClusterSnapshot",                 "redshift:DescribeClusterSnapshots",                 "sns:CreateTopic",                 "sns:DeleteTopic",                 "sns:ListSubscriptionsByTopic",                 "sns:ListTopics",                 "sns:SetTopicAttributes",                 "sns:Subscribe",                 "sns:Unsubscribe",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SetQueueAttributes"             ],             "Resource": "\*"         }     ]  } |

* IAM roles used to perform backup operations manually as described in section [Creating Redshift Backups Manually](aws_backup_manual_redshift.md):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup:DeleteRecoveryPoint",                 "backup:DescribeBackupJob",                 "backup:DescribeRecoveryPoint",                 "backup:DescribeRegionSettings",                 "backup:ListBackupVaults",                 "backup:ListTags",                 "backup:StartBackupJob",                 "backup:StopBackupJob",                 "backup:UpdateRegionSettings",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeRegions",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:SimulatePrincipalPolicy",                 "iam:PassRole",                 "redshift:CreateClusterSnapshot",                 "redshift:CreateTags",                 "redshift:DeleteTags",                 "redshift:DescribeClusters",                 "redshift:DescribeClusterSnapshots",                 "redshift:DescribeTags",                 "redshift:DeleteClusterSnapshot"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

