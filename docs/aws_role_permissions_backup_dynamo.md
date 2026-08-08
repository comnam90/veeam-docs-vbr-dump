---
title: "DynamoDB Backup IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Backup IAM Role Permissions


Backup appliances use DynamoDB Backup IAM roles to perform the following operations:

* To enumerate resources added to a backup policy.
* To create backups of DynamoDB tables.

* To create backup copies, and so on.

To perform these operations, IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [DynamoDB backup policy settings](aws_add_policy_scope_dynamo.md#account) must meet the following requirements:

1. Backup appliances must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).
2. The AWS Backup service must be granted permissions to assume the IAM roles.

To allow the AWS Backup service to assume an IAM role, configure trust relationships for the role and add the following statement to the trust policy:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": "sts:AssumeRole",             "Principal": {                 "Service": "backup.amazonaws.com"             }         }     ]  } |

To learn how to modify role trust policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/roles-managingrole-editing-console.html#roles-managingrole_edit-trust-policy).

1. The IAM roles must be granted the following permissions:

* IAM roles specified in the [backup policy settings](aws_add_policy_scope_dynamo.md#role):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup:CopyFromBackupVault",                 "backup:CopyIntoBackupVault",                 "backup:DeleteRecoveryPoint",                 "backup:DescribeBackupJob",                 "backup:DescribeCopyJob",                 "backup:DescribeRecoveryPoint",                 "backup:DescribeRegionSettings",                 "backup:ListBackupVaults",                 "backup:ListRecoveryPointsByBackupVault",                 "backup:ListTags",                 "backup:StartBackupJob",                 "backup:StartCopyJob",                 "backup:StopBackupJob",                 "backup:TagResource",                 "backup:UntagResource",                 "backup:UpdateRegionSettings",                 "dynamodb:DescribeContinuousBackups",                 "dynamodb:DescribeTable",                 "dynamodb:DescribeTimeToLive",                 "dynamodb:ListTables",                 "dynamodb:ListTagsOfResource",                 "dynamodb:StartAwsBackupJob",                 "ec2:DescribeRegions",                 "ec2:DescribeAvailabilityZones,                 "events:DeleteRule",                 "events:DescribeRule",                 "events:ListTargetsByRule",                 "events:PutRule",                 "events:PutTargets",                 "events:RemoveTargets",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:Decrypt",                 "sns:CreateTopic",                 "sns:DeleteTopic",                 "sns:ListSubscriptionsByTopic",                 "sns:ListTopics",                 "sns:SetTopicAttributes",                 "sns:Subscribe",                 "sns:Unsubscribe",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SetQueueAttributes"             ],             "Resource": "\*"         }     ]  } |

* IAM roles used to perform backup operations manually as described in section [Creating DynamoDB Backups Manually](aws_backup_manual_dynamo.md):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup-storage:MountCapsule",                 "backup:CopyFromBackupVault",                 "backup:CopyIntoBackupVault",                 "backup:CreateBackupVault",                 "backup:DeleteBackupVault",                 "backup:DeleteRecoveryPoint",                 "backup:DescribeBackupJob",                 "backup:DescribeCopyJob",                 "backup:DescribeRecoveryPoint",                 "backup:DescribeRegionSettings",                 "backup:ListBackupVaults",                 "backup:ListTags",                 "backup:StartBackupJob",                 "backup:StartCopyJob",                 "backup:StopBackupJob",                 "backup:TagResource",                 "backup:UntagResource",                 "backup:UpdateRegionSettings",                 "dynamodb:DescribeContinuousBackups",                 "dynamodb:DescribeTable",                 "dynamodb:DescribeTimeToLive",                 "dynamodb:ListTagsOfResource",                 "dynamodb:StartAwsBackupJob",                 "ec2:DescribeRegions",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:Decrypt",                 "kms:DescribeKey"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

