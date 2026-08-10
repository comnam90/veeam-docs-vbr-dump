---
title: "Worker Deployment Role Permissions in Backup Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_acc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker Deployment Role Permissions in Backup Account


The worker deployment role (service IAM role) is used to deploy worker instances in the [backup account](aws_worker_options.md#backup) to perform backup and restore operations, and to create IAM roles that are attached to the deployed instances and used by backup appliances to communicate with them. The IAM role is specified in the [worker instance settings](aws_worker_add_config_backup.md#identity) and must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ebs:ListChangedBlocks",                 "ebs:ListSnapshotBlocks",                 "ec2:AttachVolume",                 "ec2:CopySnapshot",                 "ec2:CreateKeyPair",                 "ec2:CreateSnapshot",                 "ec2:CreateTags",                 "ec2:CreateVolume",                 "ec2:DeleteKeyPair",                 "ec2:DeleteSnapshot",                 "ec2:DeleteVolume",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeImages",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInstances",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeRegions",                 "ec2:DescribeRouteTables",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSnapshots",                 "ec2:DescribeSnapshotAttribute",                 "ec2:DescribeSubnets",                 "ec2:DescribeVolumes",                 "ec2:DescribeVpcEndpoints",                 "ec2:DescribeVpcs",                 "ec2:DetachVolume",                 "ec2:GetEbsDefaultKmsKeyId",                 "ec2:ModifyInstanceAttribute",                 "ec2:ModifySnapshotAttribute",                 "ec2:ModifyVolume",                 "ec2:RunInstances",                 "ec2:StartInstances",                 "ec2:StopInstances",                 "ec2:TerminateInstances",                 "iam:AddRoleToInstanceProfile",                 "iam:AttachRolePolicy",                 "iam:CreateInstanceProfile",                 "iam:CreateRole",                 "iam:DeleteInstanceProfile",                 "iam:DeleteRole",                 "iam:DeleteRolePolicy",                 "iam:DetachRolePolicy",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetInstanceProfile",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:ListAttachedRolePolicies",                 "iam:ListInstanceProfilesForRole",                 "iam:ListRolePolicies",                 "iam:PassRole",                 "iam:PutRolePolicy",                 "iam:RemoveRoleFromInstanceProfile",                 "iam:SimulatePrincipalPolicy",                 "kinesis:CreateStream",                 "kinesis:DeleteStream",                 "kinesis:DescribeStream",                 "kinesis:PutRecord",                 "kms:CreateGrant",                 "kms:DescribeKey",                 "kms:GenerateDataKeyWithoutPlaintext",                 "kms:GetKeyPolicy",                 "kms:ListAliases",                 "kms:ListKeys",                 "kms:ReEncryptFrom",                 "kms:ReEncryptTo",                 "pricing:GetProducts",                 "servicequotas:ListServiceQuotas",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SendMessage",                 "sqs:SetQueueAttributes",                 "ssm:GetCommandInvocation",                 "ssm:GetParameter",                 "ssm:SendCommand"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-27

