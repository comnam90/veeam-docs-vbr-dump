---
title: "RDS Backup IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# RDS Backup IAM Role Permissions


Backup appliances use RDS Backup IAM roles to perform the following operations:

* To enumerate resources added to a backup policy.
* To create cloud-native snapshots of RDS resources.

* To create snapshot replicas, and so on.

|  |
| --- |
| Note |
| The same scope of permissions is required for IAM roles used to perform backup operations automatically as described in section [Creating RDS Backup Policies](aws_policies_create_rds.md), and IAM roles used to perform backup operations manually as described in section [Creating RDS Snapshots Manually](aws_snapshot_manual_rds.md). |

To perform these operations, IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [RDS backup policy settings](aws_add_policy_scope_rds.md#account) must meet the following requirements:

1. Backup appliances must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:DescribeRegions",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeVpcs",                 "events:DescribeRule",                 "events:PutRule",                 "events:PutTargets",                 "events:DeleteRule",                 "events:RemoveTargets",                 "events:ListTargetsByRule",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:SimulatePrincipalPolicy",                 "iam:ListAccountAliases",                 "kms:DescribeKey",                 "kms:CreateGrant",                 "kms:GetKeyPolicy",                 "kms:ListKeys",                 "kms:ListAliases",                 "rds:AddTagsToResource",                 "rds:ListTagsForResource",                 "rds:DescribeDBSnapshots",                 "rds:CreateDBSnapshot",                 "rds:DescribeDBInstances",                 "rds:DeleteDBSnapshot",                 "rds:ModifyDBSnapshotAttribute",                 "rds:RemoveTagsFromResource",                 "rds:CopyDBSnapshot",                 "rds:DescribeDBClusters",                 "rds:CreateDBClusterSnapshot",                 "rds:DescribeDBClusterSnapshots",                 "rds:DeleteDBClusterSnapshot",                 "rds:CopyDBClusterSnapshot",                 "rds:ModifyDBClusterSnapshotAttribute",                 "rds:DescribeDBSubnetGroups",                 "sns:ListSubscriptionsByTopic",                 "sns:DeleteTopic",                 "sns:CreateTopic",                 "sns:ListTopics",                 "sns:Unsubscribe",                 "sns:SetTopicAttributes",                 "sns:Subscribe",                 "sqs:DeleteQueue",                 "sqs:CreateQueue",                 "sqs:SetQueueAttributes",                 "sqs:DeleteMessage",                 "sqs:ListQueues",                 "sqs:ReceiveMessage"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Permissions Required to Create RDS Image-Level Backups

[Applies only to IAM roles specified in the backup policy settings] For backup appliances to be able to create [RDS image-level backups](aws_add_policy_target_settings_backups_rds.md#enable_backups), [IAM roles specified in the backup policy settings](aws_add_policy_scope_rds.md#roles) must be granted the following additional permissions to deploy worker instances in [production accounts](aws_worker_options.md#production):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:AuthorizeSecurityGroupEgress",                 "ec2:AuthorizeSecurityGroupIngress",                 "ec2:TerminateInstances",                 "ec2:StartInstances",                 "ec2:RunInstances",                 "ec2:CreateKeyPair",                 "ec2:CreateSecurityGroup",                 "ec2:CreateTags",                 "ec2:DeleteKeyPair",                 "ec2:DeleteSecurityGroup",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeImages",                 "ec2:DescribeInstances",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInternetGateways",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeRouteTables",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSubnets",                 "ec2:DescribeVpcEndpoints",                 "ec2:ModifyInstanceAttribute",                 "ec2:RevokeSecurityGroupEgress",                 "ec2:RevokeSecurityGroupIngress",                 "iam:GetInstanceProfile",                 "iam:GetRole",                 "iam:ListInstanceProfilesForRole",                 "iam:PassRole",                 "rds:DescribeOptionGroups",                 "rds:ModifyDBInstance",                 "s3:CreateBucket",                 "s3:DeleteBucket",                 "s3:DeleteObject",                 "s3:GetObject",                 "s3:ListAllMyBuckets",                 "s3:ListBucket",                 "s3:PutBucketPolicy",                 "servicequotas:listServiceQuotas",                 "ssm:GetCommandInvocation",                 "ssm:GetParameter",                 "ssm:SendCommand",                 "sqs:SendMessage"             ],             "Resource": "\*"         }     ]  } |

Page updated 2026-05-19

