---
title: "Redshift Serverless Restore IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_restore_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Restore IAM Permissions


To perform Redshift Serverless restore operations, IAM roles and IAM users specified in the [restore settings](aws_restore_account_redshift.md), or IAM roles specified in the [organization settings](aws_organization_add_settings.md), must meet the following requirements:

1. The backup appliance must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:ListAccountAliases",                 "iam:SimulatePrincipalPolicy",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeRegions",                 "ec2:DescribeVpcs",                 "ec2:DescribeSubnets",                 "ec2:DescribeSecurityGroups",                 "kms:CreateGrant",                 "kms:Decrypt",                 "kms:DescribeKey",                 "kms:GenerateDataKey",                 "kms:ListKeys",                 "kms:ListAliases",                 "iam:ListRoles",                 "iam:PassRole",                 "redshift-serverless:CreateNamespace",                 "redshift-serverless:CreateWorkgroup",                 "redshift-serverless:DeleteNamespace",                 "redshift-serverless:DeleteWorkgroup",                 "redshift-serverless:GetNamespace",                 "redshift-serverless:GetWorkgroup",                 "redshift-serverless:GetSnapshot",                 "redshift-serverless:ListNamespaces",                 "redshift-serverless:ListWorkgroups",                 "redshift-serverless:ListTagsForResource",                 "redshift-serverless:RestoreFromSnapshot",                 "redshift-serverless:TagResource",                 "secretsmanager:DescribeSecret",                 "secretsmanager:CreateSecret",                 "secretsmanager:RotateSecret",                 "secretsmanager:TagResource"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

