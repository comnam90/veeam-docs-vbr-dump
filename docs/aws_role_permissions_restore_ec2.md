---
title: "EC2 Restore IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_restore_ec2.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# EC2 Restore IAM Permissions


To perform EC2 restore operations, IAM roles and IAM users specified in the [entire EC2 instance restore settings](aws_restore_entire_account.md) and [volume-level restore settings](aws_restore_volume_account.md), or IAM roles specified in the [organization settings](aws_organization_add_settings.md), must meet the following requirements:

1. The backup appliance must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:AssignPrivateIpAddresses",                 "ec2:AssociateAddress",                 "ec2:AssociateIamInstanceProfile",                 "ec2:AllocateAddress",                 "ec2:AttachNetworkInterface",                 "ec2:AttachVolume",                 "ec2:CopySnapshot",                 "ec2:CreateNetworkInterface",                 "ec2:CreateTags",                 "ec2:CreateVolume",                 "ec2:DeleteNetworkInterface",                 "ec2:DeleteSnapshot",                 "ec2:DeleteTags",                 "ec2:DeleteVolume",                 "ec2:DescribeAddresses",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeConversionTasks",                 "ec2:DescribeImages",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInstances",                 "ec2:DescribeInstanceStatus",                 "ec2:DescribeInstanceTypes",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeNetworkInterfaces",                 "ec2:DescribeRegions",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSnapshotAttribute",                 "ec2:DescribeSnapshots",                 "ec2:DescribeSubnets",                 "ec2:DescribeVolumeAttribute",                 "ec2:DescribeVolumes",                 "ec2:DescribeVpcs",                 "ec2:DetachVolume",                 "ec2:DisassociateAddress",                 "ec2:GetEbsDefaultKmsKeyId",                 "ec2:ModifyInstanceAttribute",                 "ec2:ModifyNetworkInterfaceAttribute",                 "ec2:ModifyVolume",                 "ec2:RunInstances",                 "ec2:StartInstances",                 "ec2:StopInstances",                 "ec2:TerminateInstances",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetInstanceProfile",                 "iam:ListAccountAliases",                 "iam:listInstanceProfiles",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:CreateGrant",                 "kms:DescribeKey",                 "kms:GenerateDataKeyWithoutPlaintext",                 "kms:GetKeyPolicy",                 "kms:ListAliases",                 "kms:ListKeys",                 "kms:ReEncryptFrom",                 "kms:ReEncryptTo"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Permissions Required to Deploy Worker Instances in Production Account

If you plan to instruct the backup appliance to deploy worker instances in production accounts to perform [entire EC2 instance](aws_restore_entire_account.md#workers) or [volume-level restore](aws_restore_volume_account.md#workers), the IAM roles specified in the [entire EC2 instance](aws_restore_entire_account.md#roles) and [volume-level restore](aws_restore_volume_account.md#roles) settings must be granted the following additional permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:CreateKeyPair",                 "ec2:DeleteKeyPair",                 "ec2:DescribeAccountAttributes",                 "iam:GetRole",                 "iam:ListInstanceProfilesForRole",                 "servicequotas:ListServiceQuotas",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SendMessage",                 "sqs:SetQueueAttributes",                 "ssm:GetCommandInvocation",                 "ssm:GetParameter",                 "ssm:SendCommand"             ],             "Resource": "\*"         }     ]  } |

Page updated 2026-05-19

