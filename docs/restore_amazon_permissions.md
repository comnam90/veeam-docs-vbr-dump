---
title: "AWS IAM User Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_amazon_permissions.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# AWS IAM User Permissions

In this article

To restore to Amazon EC2, it is recommended that the IAM user whose credentials you plan to use to connect to AWS has administrative permissions — access to all AWS actions and resources.

If you do not want to provide full access to AWS, you can grant to the IAM user a minimal set of permissions that will be sufficient for restore. To do that, create the following policy in the JSON format and attach it to the IAM user.

|  |
| --- |
| Note |
| The iam: CreateRole permission is required if you want to perform restore without helper appliances. This permission is used to create a service role named vmimport required for import to Amazon EC2. If you plan to restore workloads using helper appliances, you can omit the iam: CreateRole permission. However, restore without helper appliances will fail. |

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [{    "Action": [     "ec2:DescribeInstances",     "ec2:DescribeInstanceTypes",     "ec2:RunInstances",     "ec2:TerminateInstances",     "ec2:StartInstances",     "ec2:StopInstances",     "ec2:ModifyInstanceAttribute",     "ec2:DescribeImages",     "ec2:ImportImage",     "ec2:DeregisterImage",     "ec2:DescribeVolumes",     "ec2:CreateVolume",     "ec2:ModifyVolume",     "ec2:ImportVolume",     "ec2:DeleteVolume",     "ec2:AttachVolume",     "ec2:DetachVolume",     "ec2:GetEbsEncryptionByDefault",     "ec2:CreateSnapshot",     "ec2:DescribeSnapshots",     "ec2:DeleteSnapshot",     "ec2:DescribeSubnets",     "ec2:DescribeNetworkInterfaces",     "ec2:DescribeSecurityGroups",     "ec2:DescribeKeyPairs",     "ec2:CreateKeyPair",     "ec2:DeleteKeyPair",     "ec2:DescribeAvailabilityZones",     "ec2:DescribeVpcs",     "ec2:DescribeConversionTasks",     "ec2:DescribeImportImageTasks",     "ec2:DescribeVolumesModifications",     "ec2:CancelImportTask",     "ec2:CancelConversionTask",     "ec2:CreateTags",     "ec2:DescribeAccountAttributes",     "ec2:DescribeDhcpOptions",     "ec2:DescribeVpcAttribute",     "iam:GetRole",     "iam:CreateRole",     "iam:PutRolePolicy",     "iam:DeleteRolePolicy",     "s3:CreateBucket",     "s3:ListBucket",     "s3:ListAllMyBuckets",     "s3:DeleteBucket",     "s3:PutObject",     "s3:DeleteObject",     "s3:GetBucketLocation",     "s3:PutLifeCycleConfiguration",     "s3:GetObject",     "s3:RestoreObject",     "s3:AbortMultiPartUpload",     "s3:ListBucketMultiPartUploads",     "s3:ListMultipartUploadParts"    ],    "Effect": "Allow",    "Resource": "\*"   }]  } |

Alternatively, you can attach the created policy to the IAM group or role to which the IAM user is assigned.

For information on how to create and attach a policy to an IAM user, see the [Creating IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) and [Adding and Removing IAM Identity Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) sections in the AWS IAM User Guide.

Page updated 3/11/2025

Page content applies to build 13.0.1.1071
