---
title: "EC2 Backup IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_ec2.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# EC2 Backup IAM Role Permissions


Backup appliances use EC2 Backup IAM roles to perform the following operations:

* To enumerate resources added to a backup policy.
* To create cloud-native snapshots of EC2 instances.
* To create snapshot replicas, and so on.

|  |
| --- |
| Note |
| The same scope of permissions is required for IAM roles used to perform backup operations automatically as described in section [Creating EC2 Backup Policies](aws_policies_create.md), and IAM roles used to perform backup operations manually as described in section [Creating EC2 Snapshots Manually](aws_snapshot_manual.md). |

To perform these operations, IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [EC2 backup policy settings](aws_add_policy_scope.md#account) must meet the following requirements:

1. Backup appliances must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ebs:GetSnapshotBlock",                 "ebs:ListSnapshotBlocks",                 "ebs:ListChangedBlocks",                 "ec2:CreateSnapshots",                 "ec2:CreateSnapshot",                 "ec2:CopySnapshot",                 "ec2:CreateTags",                 "ec2:DescribeInstanceAttribute",                 "ec2:DeleteSnapshot",                 "ec2:DescribeSnapshotAttribute",                 "ec2:DescribeInstances",                 "ec2:DeleteTags",                 "ec2:DescribeRegions",                 "ec2:DescribeSnapshots",                 "ec2:DescribeVpcs",                 "ec2:DescribeImages",                 "ec2:ModifySnapshotAttribute",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeVolumes",                 "ec2:DescribeInstanceTypes",                 "ec2:DescribeAddresses",                 "ec2:DescribeNetworkInterfaces",                 "ec2:DescribeSubnets",                 "ec2:DescribeConversionTasks",                 "ec2:DescribeVolumeAttribute",                 "ec2:DescribeTags",                 "ec2:GetEbsDefaultKmsKeyId",                 "events:DescribeRule",                 "events:RemoveTargets",                 "events:PutTargets",                 "events:DeleteRule",                 "events:ListTargetsByRule",                 "events:PutRule",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetInstanceProfile",                 "iam:SimulatePrincipalPolicy",                 "iam:ListAccountAliases",                 "iam:ListInstanceProfiles",                 "kms:Decrypt",                 "kms:ListKeys",                 "kms:ListAliases",                 "kms:GetKeyPolicy",                 "kms:ReEncryptTo",                 "kms:DescribeKey",                 "kms:ReEncryptFrom",                 "kms:CreateGrant",                 "servicequotas:ListServiceQuotas",                 "sqs:DeleteMessage",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:DeleteQueue",                 "sqs:CreateQueue",                 "sqs:SetQueueAttributes",                 "sns:ListSubscriptionsByTopic",                 "sns:DeleteTopic",                 "sns:CreateTopic",                 "sns:ListTopics",                 "sns:Unsubscribe",                 "sns:SetTopicAttributes",                 "sns:Subscribe",                 "ssm:SendCommand",                 "ssm:GetCommandInvocation",                 "ssm:DescribeInstanceInformation"                            ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Permissions Required to Deploy Worker Instances in Production Account

[Applies only to IAM roles specified in the backup policy settings] If you plan to instruct backup appliances to deploy worker instances in [production accounts](aws_worker_options.md#production), [IAM roles specified in the backup policy settings](aws_add_policy_scope.md#role) must be granted the following additional permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:AttachVolume",                 "ec2:CreateKeyPair",                 "ec2:CreateVolume",                 "ec2:DeleteKeyPair",                 "ec2:DeleteVolume",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeSecurityGroups",                 "ec2:DetachVolume",                 "ec2:ModifyInstanceAttribute",                 "ec2:RunInstances",                 "ec2:TerminateInstances",                 "iam:GetRole",                 "iam:ListInstanceProfilesForRole",                 "iam:PassRole",                 "ssm:GetParameter",                 "sqs:SendMessage"             ],             "Resource": "\*"         }     ]  } |

Page updated 2026-07-21

