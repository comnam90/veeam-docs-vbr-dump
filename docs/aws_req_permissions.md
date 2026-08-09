---
title: "Plug-In Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_req_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Plug-In Permissions


To perform backup and restore operations, accounts that Veeam Plug-in for AWS uses to perform data protection and disaster recovery operations must be granted the following permissions.

Veeam Backup & Replication User Account Permissions

A user account that you plan to use when installing and working with Veeam Backup & Replication must have permissions described in section [Installing and Using Veeam Backup & Replication](required_permissions.md).

Backup Appliance User Account Permissions

A user account that Veeam Backup & Replication will use to authenticate against the backup appliance and get access to the appliance functionality must be assigned the Portal Administrator role. For more information on user roles, see [Managing User Accounts](aws_accounts_vba_users.md).

|  |
| --- |
| Note |
| When you deploy a backup appliance from the Veeam Backup & Replication console, Veeam Backup & Replication will automatically create the necessary user account that will be assigned all the required permissions. |

AWS IAM User Permissions

Veeam Plug-in for AWS requires the following [IAM identities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html):

* An IAM user whose permissions are used to create, connect and manage backup appliances. To be able to perform these operations, the specified IAM user must have the following set of permissions:

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to deploy a new backup appliance

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Sid": "CreateResources",             "Effect": "Allow",             "Action": [                "cloudwatch:PutMetricAlarm",                "ec2:AllocateAddress",                "ec2:AssociateAddress",                "ec2:AttachInternetGateway",                "ec2:AuthorizeSecurityGroupIngress",                "ec2:CreateInternetGateway",                "ec2:CreateKeyPair",                "ec2:CreateRoute",                "ec2:CreateSecurityGroup",                "ec2:CreateSnapshot",                "ec2:CreateSubnet",                "ec2:CreateTags",                "ec2:CreateVpc",                "ec2:DeleteSnapshot",                "ec2:DescribeAddresses",                "ec2:DescribeAvailabilityZones",                "ec2:DescribeIamInstanceProfileAssociations",                "ec2:DescribeInstanceAttribute",                "ec2:DescribeImages",                "ec2:DescribeInstanceTypes",                "ec2:DescribeInstances",                "ec2:DescribeInternetGateways",                "ec2:DescribeKeyPairs",                "ec2:DescribeManagedPrefixLists",                "ec2:DescribeRegions",                "ec2:DescribeRouteTables",                "ec2:DescribeSecurityGroups",                "ec2:DescribeSnapshots",                "ec2:DescribeSubnets",                "ec2:DescribeVolumes",                "ec2:DescribeVpcs",                "ec2:ModifyInstanceAttribute",                "ec2:GetManagedPrefixListEntries",                "ec2:ModifyNetworkInterfaceAttribute",                "ec2:ModifySubnetAttribute",                "ec2:ModifyVpcAttribute",                "ec2:RunInstances",                "iam:AddRoleToInstanceProfile",                "iam:AttachRolePolicy",                "iam:CreateInstanceProfile",                "iam:CreatePolicy",                "iam:CreatePolicyVersion",                "iam:CreateRole",                "iam:CreateServiceLinkedRole",                "iam:DetachRolePolicy",                "iam:GetAccountSummary",                "iam:GetInstanceProfile",                "iam:GetPolicy",                "iam:GetPolicyVersion",                "iam:GetRole",                "iam:ListAttachedRolePolicies",                "iam:ListInstanceProfilesForRole",                "iam:ListPolicyVersions",                "iam:ListRolePolicies",                "iam:PassRole",                "iam:PutRolePolicy",                "s3:CreateBucket",                "s3:DeleteBucket",                "s3:DeleteObject",                "s3:GetObject",                "s3:ListAllMyBuckets",                "s3:ListBucket",                "s3:PutObject",                "servicequotas:ListServiceQuotas",                "ssm:DescribeInstanceInformation",                "ssm:GetCommandInvocation",                "ssm:GetParameter",                "ssm:SendCommand"             ],             "Resource": "\*"         },         {             "Sid": "CleanupResources",             "Effect": "Allow",             "Action": [                "cloudwatch:DeleteAlarms",                "ec2:DeleteInternetGateway",                "ec2:DeleteSecurityGroup",                "ec2:DeleteSubnet",                "ec2:DeleteVpc",                "ec2:DetachInternetGateway",                "ec2:DisassociateAddress",                "ec2:ReleaseAddress",                "ec2:TerminateInstances",                "iam:DeleteInstanceProfile",                "iam:DeletePolicy",                "iam:DeletePolicyVersion",                "iam:DeleteRole",                "iam:DeleteRolePolicy",                "iam:DetachRolePolicy",                "iam:RemoveRoleFromInstanceProfile"             ],             "Resource": [                 "\*"             ]         }     ]  } | |

|  |
| --- |
| Note |
| If EBS encryption by default is enabled for your AWS account, all the newly created volumes will be encrypted using the default KMS key specified in the EC2 console. Therefore, for the IAM user to be able to encrypt the EBS volumes of the appliance, the following conditions must be met:   * The IAM user must have permissions to use the KMS key specified for EBS encryption by default. * The IAM user must be assigned the kms:GenerateDataKeyWithoutPlaintext permission.   For more information on EBS encryption, see [AWS Documentation](https://docs.aws.amazon.com/ebs/latest/userguide/encryption-by-default.html). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to connect an existing backup appliance

|  |  |
| --- | --- |
| |  | | --- | | {   "Version": "2012-10-17",   "Statement": [    {             "Effect": "Allow",             "Action": [                "ec2:AttachVolume",                "ec2:CreateSnapshot",                "ec2:CreateTags",                "ec2:CreateVolume",                "ec2:DeleteSnapshot",                "ec2:DeleteVolume",                "ec2:DescribeAddresses",                "ec2:DescribeAvailabilityZones",                "ec2:DescribeIamInstanceProfileAssociations",                "ec2:DescribeInstanceAttribute",                "ec2:DescribeInstances",                "ec2:DescribeRegions",                "ec2:DescribeSnapshots",                "ec2:DescribeVolumes",                "ec2:DetachVolume",                "ec2:ModifyInstanceAttribute",                "ec2:StartInstances",                "ec2:StopInstances",                "iam:AddRoleToInstanceProfile",                "iam:AttachRolePolicy",                "iam:CreateInstanceProfile",                "iam:CreatePolicy",                "iam:CreatePolicyVersion",                "iam:DetachRolePolicy",                "iam:GetAccountSummary",                "iam:GetInstanceProfile",                "iam:GetPolicy",                "iam:GetPolicyVersion",                "iam:GetRole",                "iam:ListAttachedRolePolicies",                "iam:ListInstanceProfilesForRole",                "iam:ListPolicyVersions",                "iam:ListRolePolicies",                "iam:PassRole",                "iam:UpdateAssumeRolePolicy"             ],             "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to add a repository

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:DescribeRegions",                 "ec2:DescribeAddresses",                 "ec2:DescribeInstances",                 "iam:GetRole",                 "iam:SimulatePrincipalPolicy",                 "s3:CreateBucket",                 "s3:DeleteObject",                 "s3:DeleteObjectVersion",                 "s3:GetBucketLocation",                 "s3:GetBucketVersioning",                 "s3:GetBucketObjectLockConfiguration",                 "s3:GetObject",                 "s3:GetObjectVersion",                 "s3:GetObjectRetention",                 "s3:ListBucket",                 "s3:ListAllMyBuckets",                 "s3:ListBucketVersions",                 "s3:PutBucketVersioning",                 "s3:PutBucketObjectLockConfiguration",                 "s3:PutObjectRetention",                 "s3:PutObject"             ],             "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to encrypt repositories using AWS KMS keys

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "kms:Decrypt",                 "kms:DescribeKey",                 "kms:Encrypt",                 "kms:ListAliases",                 "kms:ListKeys"             ],             "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to upgrade backup appliance to version 11

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "ec2:AssociateIamInstanceProfile",                 "ec2:AttachVolume",                 "ec2:CreateSnapshot",                 "ec2:CreateTags",                 "ec2:CreateVolume",                 "ec2:DeleteSnapshot",                 "ec2:DeleteVolume",                 "ec2:DescribeAddresses",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeIamInstanceProfileAssociations",                 "ec2:DescribeImages",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInstances",                 "ec2:DescribeNetworkInterfaces",                 "ec2:DescribeRegions",                 "ec2:DescribeSnapshots",                 "ec2:DescribeVolumeAttribute",                 "ec2:DescribeVolumes",                 "ec2:DetachVolume",                 "ec2:DisassociateIamInstanceProfile",                 "ec2:ModifyInstanceAttribute",                 "ec2:ModifyNetworkInterfaceAttribute",                 "ec2:RunInstances",                 "ec2:StartInstances",                 "ec2:StopInstances",                 "ec2:TerminateInstances",                 "iam:AttachRolePolicy",                 "iam:DetachRolePolicy",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetInstanceProfile",                 "iam:GetRole",                 "iam:ListAttachedRolePolicies",                 "iam:ListInstanceProfiles",                 "iam:PassRole",                 "iam:SimulatePrincipalPolicy",                 "s3:CreateBucket",                 "s3:DeleteBucket",                 "s3:DeleteObject",                 "s3:GetObject",                 "s3:ListAllMyBuckets",                 "s3:ListBucket",                 "s3:PutBucketAcl",                 "s3:PutObject",                 "ssm:DescribeInstanceInformation",                 "ssm:GetCommandInvocation",                 "ssm:GetParameter",                 "ssm:SendCommand",                 "sts:GetCallerIdentity"             ],             "Resource": "\*"         }     ]  } | |

|  |
| --- |
| Note |
| For Veeam Backup & Replication to be able to upgrade permissions of the [Default Backup Restore IAM role](aws_deploying_appliances.md#roles) when upgrading to version 9, add the necessary permissions listed below to the IAM policy attached to the Default Backup Restore IAM role. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)List of permissions to upgrade the Default Backup Restore IAM role

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "iam:AddRoleToInstanceProfile",                 "iam:AttachRolePolicy",                 "iam:CreateInstanceProfile",                 "iam:CreatePolicy",                 "iam:CreatePolicyVersion",                 "iam:DetachRolePolicy",                 "iam:GetAccountSummary",                 "iam:GetInstanceProfile",                 "iam:GetPolicy",                 "iam:GetPolicyVersion",                 "iam:GetRole",                 "iam:ListAttachedRolePolicies",                 "iam:ListInstanceProfilesForRole",                 "iam:ListPolicyVersions",                 "iam:PassRole",                 "iam:UpdateAssumeRolePolicy"             ],             "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Full list of permissions

|  |  |
| --- | --- |
| |  | | --- | | {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "cloudwatch:DeleteAlarms",                 "cloudwatch:PutMetricAlarm",                 "ec2:AllocateAddress",                 "ec2:AssociateAddress",                 "ec2:AssociateIamInstanceProfile",                 "ec2:AttachInternetGateway",                 "ec2:AttachVolume",                 "ec2:AuthorizeSecurityGroupIngress",                 "ec2:CreateInternetGateway",                 "ec2:CreateKeyPair",                 "ec2:CreateRoute",                 "ec2:CreateSecurityGroup",                 "ec2:CreateSnapshot",                 "ec2:CreateSubnet",                 "ec2:CreateTags",                 "ec2:CreateVolume",                 "ec2:CreateVpc",                 "ec2:DeleteInternetGateway",                 "ec2:DeleteSecurityGroup",                 "ec2:DeleteSnapshot",                 "ec2:DeleteSubnet",                 "ec2:DeleteVolume",                 "ec2:DeleteVpc",                 "ec2:DescribeAddresses",                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeIamInstanceProfileAssociations",                 "ec2:DescribeImages",                 "ec2:DescribeInstanceAttribute",                 "ec2:DescribeInstances",                 "ec2:DescribeInstanceTypes",                 "ec2:DescribeInternetGateways",                 "ec2:DescribeKeyPairs",                 "ec2:DescribeManagedPrefixLists",                 "ec2:DescribeNetworkInterfaces",                 "ec2:DescribeRegions",                 "ec2:DescribeRouteTables",                 "ec2:DescribeSecurityGroups",                 "ec2:DescribeSnapshots",                 "ec2:DescribeSubnets",                 "ec2:DescribeVolumeAttribute",                 "ec2:DescribeVolumes",                 "ec2:DescribeVpcs",                 "ec2:DetachInternetGateway",                 "ec2:DetachVolume",                 "ec2:DisassociateAddress",                 "ec2:DisassociateIamInstanceProfile",                 "ec2:GetManagedPrefixListEntries",                 "ec2:ModifyInstanceAttribute",                 "ec2:ModifyNetworkInterfaceAttribute",                 "ec2:ModifySubnetAttribute",                 "ec2:ModifyVpcAttribute",                 "ec2:ReleaseAddress",                 "ec2:RunInstances",                 "ec2:StartInstances",                 "ec2:StopInstances",                 "ec2:TerminateInstances",                 "iam:AddRoleToInstanceProfile",                 "iam:AttachRolePolicy",                 "iam:CreateInstanceProfile",                 "iam:CreatePolicy",                 "iam:CreatePolicyVersion",                 "iam:CreateRole",                 "iam:CreateServiceLinkedRole",                 "iam:DeleteInstanceProfile",                 "iam:DeletePolicy",                 "iam:DeletePolicyVersion",                 "iam:DeleteRole",                 "iam:DeleteRolePolicy",                 "iam:DetachRolePolicy",                 "iam:GetAccountSummary",                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:GetInstanceProfile",                 "iam:GetPolicy",                 "iam:GetPolicyVersion",                 "iam:GetRole",                 "iam:ListAttachedRolePolicies",                 "iam:ListInstanceProfiles",                 "iam:ListInstanceProfilesForRole",                 "iam:ListPolicyVersions",                 "iam:ListRolePolicies",                 "iam:PassRole",                 "iam:PutRolePolicy",                 "iam:RemoveRoleFromInstanceProfile",                 "iam:SimulatePrincipalPolicy",                 "iam:UpdateAssumeRolePolicy",                 "kms:Decrypt",                 "kms:DescribeKey",                 "kms:Encrypt",                 "kms:ListAliases",                 "kms:ListKeys",                 "s3:CreateBucket",                 "s3:DeleteBucket",                 "s3:DeleteObject",                 "s3:DeleteObjectVersion",                 "s3:GetBucketLocation",                 "s3:GetBucketObjectLockConfiguration",                 "s3:GetBucketVersioning",                 "s3:GetObject",                 "s3:GetObjectRetention",                 "s3:GetObjectVersion",                 "s3:ListAllMyBuckets",                 "s3:ListBucket",                 "s3:ListBucketVersions",                 "s3:PutBucketAcl",                 "s3:PutBucketObjectLockConfiguration",                 "s3:PutBucketVersioning",                 "s3:PutObject",                 "s3:PutObjectRetention",                 "servicequotas:ListServiceQuotas",                 "ssm:DescribeInstanceInformation",                 "ssm:GetCommandInvocation",                 "ssm:GetParameter",                 "ssm:SendCommand",                 "sts:GetCallerIdentity"           ],             "Resource": "\*"         }     ]  } | |

|  |
| --- |
| Important |
| Note that the following permissions are only required to remove created resources during appliance deployment in case of deployment failure or removal of the backup appliance from the backup infrastructure: ec2:DeleteSubnet, ec2:DeleteSecurityGroup, ec2:DetachInternetGateway, ec2:DeleteInternetGateway, ec2:DeleteVpc. If you have not added these permissions for security reasons, remove the resources manually using the AWS Management Console as described in [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html). |

* IAM roles whose permissions are used to perform data protection and disaster recovery operations with AWS resources.

When you deploy a new backup appliance, the [Default Backup Restore IAM role](aws_deploying_appliances.md) is automatically created and added to the appliance. The Default Backup Restore IAM role is assigned all permissions required to perform data protection and disaster recovery operations in the same AWS account where the backup appliance resides. For more information on the Default Backup Restore IAM role permissions, see [Full List of IAM Permissions](aws_full_list_permissions.md). However, you can create additional IAM roles with granular permissions and add them to the appliance as described in section [Managing IAM Roles](aws_accounts_iam_roles.md).

* IAM users whose access keys are specified to access standard backup repositories where the image-level backups are stored must have permissions described in the [Using Amazon S3 Object Storage](required_permissions.md) section if plan to [copy image-level backups](aws_backup_copy.md) or to [restore guest OS files from image-level backups](aws_guest_file_recovery.md). To learn how to specify access keys of IAM users, see sections [Connecting to Existing Appliance](aws_connect_appliance_repo.md) and [Creating New Repositories](aws_add_s3_account.md).
* IAM users whose one-time access keys are used to automatically grant missing permissions to IAM users must have the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "iam:AttachUserPolicy",                 "iam:CreatePolicy",                 "iam:GetAccountSummary",                 "iam:GetPolicy",                 "iam:GetPolicyVersion"             ],             "Resource": "\*"         }     ]  } |

Veeam Backup & Replication neither saves nor stores these one-time access keys in the appliance configuration database.

Virtualization Servers and Hosts Service Account Permissions

If you plan to copy backups to on-premises backup repositories, to perform restore to VMware vSphere and Microsoft Hyper-V environments, or to perform other tasks related to virtualization servers and hosts, you must check whether the service account specified for these servers and hosts has the required permissions described in section [Permissions](required_permissions.md).

Microsoft Azure Account Permissions

An Azure AD application that you plan to use to restore EC2 instances to Microsoft Azure must have permissions described in section [Permissions](required_permissions.md).

Google Cloud Service Account Permissions

A service account that you plan to use to restore EC2 instances to Google Cloud must have permissions described in section [Google Compute Engine IAM User Permissions](gcp_iam_permissions.md).

Page updated 2026-05-26

