---
title: "FLR Worker IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_flr_prod.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# FLR Worker IAM Role Permissions


To allow a backup appliance to deploy worker instances in production accounts to perform EC2 file-level recovery operations, attach IAM roles to the instances and further to communicate with these instances, [IAM roles specified in the file-level recovery settings](aws_restore_item_mode.md#workers) must meet the following requirements:

1. The IAM roles must be included at least in one instance profile. For more information on instance profiles, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html).
2. The backup appliance must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md#reqs).
3. The Amazon EC2 service must be granted permissions to assume the IAM roles.

To allow the Amazon EC2 service to assume an IAM role, configure trust relationships for the role and add the following statement to the trust policy:

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": "sts:AssumeRole",       "Principal": {         "Service": "ec2.amazonaws.com"       }     }   ]  } |

To learn how to modify role trust policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/roles-managingrole-editing-console.html#roles-managingrole_edit-trust-policy).

1. The IAM roles must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:AttachNetworkInterface",                 "ec2:AttachVolume",                 "ec2:CopySnapshot",                 "ec2:CreateKeyPair",                 "ec2:CreateNetworkInterface",                 "ec2:CreateSnapshot",                 "ec2:CreateTags",                 "ec2:CreateVolume",                 "ec2:DeleteKeyPair",                 "ec2:DeleteNetworkInterface",                 "ec2:DeleteSnapshot",                 "ec2:DeleteVolume",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeAddresses",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInstances",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeNetworkInterfaces",                 "ec2:DescribeRegions",                 "ec2:DescribeRouteTables",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSnapshotAttribute",                 "ec2:DescribeSnapshots",                 "ec2:DescribeSubnets",                 "ec2:DescribeVolumeAttribute",                 "ec2:DescribeVolumes",                 "ec2:DescribeVpcs",                 "ec2:DetachVolume",                 "ec2:ModifyInstanceAttribute",                 "ec2:RunInstances",                 "ec2:StartInstances",                 "ec2:StopInstances",                 "ec2:TerminateInstances",                 "ec2messages:AcknowledgeMessage",                 "ec2messages:DeleteMessage",                 "ec2messages:FailMessage",                 "ec2messages:GetEndpoint",                 "ec2messages:GetMessages",                 "ec2messages:SendReply",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetRole",                 "iam:ListAccountAliases",                 "iam:ListInstanceProfilesForRole",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "kms:CreateGrant",                 "kms:DescribeKey",                 "kms:GetKeyPolicy",                 "kms:ListAliases",                 "kms:ListKeys",                 "kms:ReEncryptFrom",                 "kms:ReEncryptTo",                 "servicequotas:ListServiceQuotas",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SetQueueAttributes",                 "sqs:SendMessage",                 "ssm:DescribeAssociation",                 "ssm:DescribeDocument",                 "ssm:GetCommandInvocation",                 "ssm:GetDeployablePatchSnapshotForInstance",                 "ssm:GetDocument",                 "ssm:GetManifest",                 "ssm:GetParameter",                 "ssm:GetParameters",                 "ssm:ListAssociations",                 "ssm:ListInstanceAssociations",                 "ssm:PutComplianceItems",                 "ssm:PutConfigurePackageResult",                 "ssm:PutInventory",                 "ssm:SendCommand",                 "ssm:UpdateAssociationStatus",                 "ssm:UpdateInstanceAssociationStatus",                 "ssm:UpdateInstanceInformation",                 "ssmmessages:CreateControlChannel",                 "ssmmessages:CreateDataChannel",                 "ssmmessages:OpenControlChannel",                 "ssmmessages:OpenDataChannel"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

