---
title: "DynamoDB Restore IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_restore_dynamo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# DynamoDB Restore IAM Permissions


To perform DynamoDB restore operations, IAM roles and IAM users specified in the [restore settings](aws_restore_account_dynamo.md), or IAM roles specified in the [organization settings](aws_organization_add_settings.md), must meet the following requirements:

1. The backup appliance must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).
2. The AWS Backup service must be granted permissions to assume the IAM roles.

To allow the AWS Backup service to assume an IAM role, configure trust relationships for the role and add the following statement to the trust policy:

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": "sts:AssumeRole",       "Principal": {         "Service": "backup.amazonaws.com"       }     }   ]  } |

To learn how to modify role trust policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/roles-managingrole-editing-console.html#roles-managingrole_edit-trust-policy).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup-storage:MountCapsule",                 "backup:CopyFromBackupVault",                 "backup:CopyIntoBackupVault",                 "backup:CreateBackupVault",                 "backup:DeleteBackupVault",                 "backup:DeleteRecoveryPoint",                 "backup:DescribeCopyJob",                 "backup:DescribeRecoveryPoint",                 "backup:DescribeRestoreJob",                 "backup:ListBackupVaults",                 "backup:ListTags",                 "backup:StartCopyJob",                 "backup:StartRestoreJob",                 "backup:TagResource",                 "dynamodb:DeleteTable",                 "dynamodb:DescribeContinuousBackups",                 "dynamodb:DescribeTable",                 "dynamodb:DescribeTimeToLive",                 "dynamodb:ListTables",                 "dynamodb:RestoreTableFromAwsBackup",                 "dynamodb:TagResource",                 "dynamodb:UpdateContinuousBackups",                 "dynamodb:UpdateTable",                 "dynamodb:UpdateTimeToLive",                 "ec2:DescribeRegions",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:CreateGrant",                 "kms:Decrypt",                 "kms:DescribeKey",                 "kms:ListAliases",                 "kms:ListKeys"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

