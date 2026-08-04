---
title: "Redshift Serverless Backup IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Backup IAM Role Permissions


Backup appliances use Redshift Serverless Backup IAM roles to perform the following operations:

* To enumerate resources added to a backup policy.
* To create backups of Redshift Serverless namespaces.

To perform these operations, IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [Redshift Serverless backup policy settings](aws_add_policy_scope_redshift_serverless.md#account) must meet the following requirements:

1. Backup appliances must be granted permissions to assume the IAM roles. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM roles must be granted the following permissions:

* IAM roles specified in the [backup policy settings](aws_add_policy_scope_redshift_serverless.md#role):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeRegions",                 "redshift-serverless:CreateSnapshot",                 "redshift-serverless:DeleteSnapshot",                 "redshift-serverless:GetSnapshot",                 "redshift-serverless:ListNamespaces",                 "redshift-serverless:ListWorkgroups",                 "redshift-serverless:ListTagsForResource",                 "redshift-serverless:ListSnapshots",                 "redshift-serverless:TagResource",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:SimulatePrincipalPolicy",                 "iam:ListAccountAliases",                 "kms:DescribeKey",                 "events:DeleteRule",                 "events:DescribeRule",                 "events:ListTargetsByRule",                 "events:PutRule",                 "events:PutTargets",                 "events:RemoveTargets",                 "sns:CreateTopic",                 "sns:DeleteTopic",                 "sns:ListSubscriptionsByTopic",                 "sns:ListTopics",                 "sns:SetTopicAttributes",                 "sns:Subscribe",                 "sns:Unsubscribe",                 "sqs:CreateQueue",                 "sqs:DeleteMessage",                 "sqs:DeleteQueue",                 "sqs:ListQueues",                 "sqs:ReceiveMessage",                 "sqs:SetQueueAttributes"             ],             "Resource": "\*"         }     ]  } |

* IAM roles used to perform backup operations manually as described in section [Creating Redshift Serverless Backups Manually](aws_backup_manual_redshift_serverless.md):

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeRegions",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:ListAccountAliases",                 "iam:SimulatePrincipalPolicy",                 "redshift-serverless:CreateSnapshot",                 "redshift-serverless:DeleteSnapshot",                 "redshift-serverless:GetSnapshot",                 "redshift-serverless:ListNamespaces",                 "redshift-serverless:ListWorkgroups",                 "redshift-serverless:ListTagsForResource",                 "redshift-serverless:ListSnapshots",                 "redshift-serverless:TagResource",                 "kms:DescribeKey"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

