---
title: "Redshift Cluster Restore IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_restore_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Cluster Restore IAM Permissions


To perform Redshift restore operations, IAM roles and IAM users specified in the [restore settings](aws_restore_account_redshift.md), or IAM roles specified in the [organization settings](aws_organization_add_settings.md), must meet the following requirements:

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
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "backup:DescribeRestoreJob",                 "backup:ListTags",                 "backup:StartRestoreJob",                 "ec2:DescribeInternetGateways",                 "ec2:DescribeRegions",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSubnets",                 "ec2:DescribeVpcs",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:ListRoles",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:CreateGrant",                 "kms:Decrypt",                 "kms:DescribeKey",                 "kms:GenerateDataKey",                 "kms:ListAliases",                 "kms:ListKeys",                 "redshift:CreateTags",                 "redshift:DeleteCluster",                 "redshift:DescribeClusterParameterGroups",                 "redshift:DescribeClusters",                 "redshift:DescribeClusterSnapshots",                 "redshift:DescribeClusterSubnetGroups",                 "redshift:DescribeNodeConfigurationOptions",                 "redshift:DescribeTags",                 "redshift:ModifyCluster",                 "redshift:RestoreFromClusterSnapshot",                 "secretsmanager:CreateSecret",                 "secretsmanager:DescribeSecret",                 "secretsmanager:TagResource"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

