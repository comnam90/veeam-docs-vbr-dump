---
title: "Object Storage Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_object_storage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Object Storage Repositories


General Amazon S3 and S3 Compatible Object Storage Permissions

Consider the following:

* The permissions listed in the section for Amazon S3 and S3 Compatible are IAM policy actions. These may differ from the S3 API operation names used in the AWS SDK or API documentation. For more information, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-with-s3-policy-actions.html#using-with-s3-policy-actions-related-to-buckets).
* Use the account that has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the [New Object Repository](adding_amazon_object_storage.md) wizard.

Permissions for Amazon S3 or S3 compatible object storage depend on whether you use [immutability](immutability_sobr.md) and [helper appliance](amazon_storage_mount_server.md#helper) settings.

|  |
| --- |
| Note |
| Consider the following:   * S3 compatible object storage repositories use the same permissions as Amazon S3 object storage with the following exception: since you cannot setup a helper appliance in the cloud, you do not need permissions for it. Therefore, S3 compatible object storage repositories require permissions which start with s3, for example, "s3:ListBucket". Permissions that start with ec2 can be skipped, for example, "ec2:DescribeInstances". * To deploy S3 compatible object storage in multiple bucket mode, you must add the s3:CreateBucket and s3:DeleteBucket permissions to the list of permissions that you are going to use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Disabled and Helper Appliance not Used

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. A helper appliance is not used for health check operations.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [          {              "Effect": "Allow",              "Action": [                "s3:ListBucket",                "s3:GetBucketLocation",                "s3:GetObject",                "s3:PutObject",                "s3:DeleteObject",                "s3:ListAllMyBuckets",                "s3:GetBucketVersioning",                "s3:GetBucketObjectLockConfiguration"              ],              "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled and New Helper Appliance Configured

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. For health check operations a new helper appliance is configured and the Amazon VPC, subnet and security group settings are set to (Create new) for the [helper appliance settings](amazon_storage_mount_server.md#helper).  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [      {          "Effect": "Allow",          "Action": [          "s3:ListBucket",          "s3:GetBucketLocation",          "s3:GetObject",          "s3:PutObject",          "s3:DeleteObject",          "s3:ListAllMyBuckets",          "s3:GetBucketVersioning",          "s3:GetBucketObjectLockConfiguration",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs",          "ec2:CreateVpc",          "ec2:CreateSubnet",          "ec2:DescribeAvailabilityZones",          "ec2:CreateRoute",          "ec2:CreateInternetGateway",          "ec2:AttachInternetGateway",          "ec2:ModifyVpcAttribute",          "ec2:CreateSecurityGroup",          "ec2:DeleteSecurityGroup",          "ec2:AuthorizeSecurityGroupIngress",          "ec2:AuthorizeSecurityGroupEgress",          "ec2:DescribeRouteTables",          "ec2:DescribeInstanceTypes"              ],          "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Immutability Disabled and Helper Appliance Configured Beforehand

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. Amazon VPC, subnet and security group settings for a helper appliance are configured beforehand.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [      {          "Effect": "Allow",          "Action": [          "s3:ListBucket",          "s3:GetBucketLocation",          "s3:GetObject",          "s3:PutObject",          "s3:DeleteObject",          "s3:ListAllMyBuckets",          "s3:GetBucketVersioning",         "s3:GetBucketObjectLockConfiguration",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs"              ],          "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)4. Immutability Enabled and Helper Appliance not Used

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. A helper appliance is not used for health check operations.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [          {              "Effect": "Allow",              "Action": [                  "s3:ListBucket",                  "s3:GetBucketLocation",                  "s3:GetObject",                  "s3:PutObject",                  "s3:DeleteObject",                  "s3:ListAllMyBuckets",                  "s3:GetBucketVersioning",                  "s3:GetBucketObjectLockConfiguration",                  "s3:ListBucketVersions",                  "s3:GetObjectVersion",                  "s3:GetObjectRetention",                  "s3:GetObjectLegalHold",                  "s3:PutObjectRetention",                  "s3:PutObjectLegalHold",                  "s3:DeleteObjectVersion"                      ],              "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)5. Immutability Enabled and New Helper Appliance Configured

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. For health check operations a new helper appliance is configured and the Amazon VPC, subnet and security group settings are set to (Create new) for the [helper appliance settings](amazon_storage_mount_server.md#helper).  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [      {          "Effect": "Allow",          "Action": [          "s3:ListBucket",          "s3:GetBucketLocation",          "s3:GetObject",          "s3:PutObject",          "s3:DeleteObject",          "s3:ListAllMyBuckets",          "s3:GetBucketVersioning",          "s3:GetBucketObjectLockConfiguration",          "s3:ListBucketVersions",          "s3:GetObjectVersion",          "s3:GetObjectRetention",          "s3:GetObjectLegalHold",          "s3:PutObjectRetention",          "s3:PutObjectLegalHold",          "s3:DeleteObjectVersion",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs",          "ec2:CreateVpc",          "ec2:CreateSubnet",          "ec2:DescribeAvailabilityZones",          "ec2:CreateRoute",          "ec2:CreateInternetGateway",          "ec2:AttachInternetGateway",          "ec2:ModifyVpcAttribute",          "ec2:CreateSecurityGroup",          "ec2:DeleteSecurityGroup",          "ec2:AuthorizeSecurityGroupIngress",          "ec2:AuthorizeSecurityGroupEgress",          "ec2:DescribeRouteTables",          "ec2:DescribeInstanceTypes"              ],          "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)6. Immutability Enabled and Helper Appliance Configured Beforehand

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. Amazon VPC, subnet and security group settings for a helper appliance are configured beforehand.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [      {          "Effect": "Allow",          "Action": [          "s3:ListBucket",          "s3:GetBucketLocation",          "s3:GetObject",          "s3:PutObject",          "s3:DeleteObject",          "s3:ListAllMyBuckets",          "s3:GetBucketVersioning",          "s3:GetBucketObjectLockConfiguration",          "s3:ListBucketVersions",          "s3:GetObjectVersion",          "s3:GetObjectRetention",          "s3:GetObjectLegalHold",          "s3:PutObjectRetention",          "s3:PutObjectLegalHold",          "s3:DeleteObjectVersion",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs"              ],          "Resource": "\*"          }      ]  } | |

For more information on permissions, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-with-s3-actions.html).

Amazon S3 Glacier and S3 Compatible with Data Archiving Object Storage Permissions

Permissions for Amazon S3 Glacier and S3 Compatible with data archiving depend on whether you use [immutability](immutability_sobr.md) and the [archiver appliance](glacier_archiver_appliance.md) settings:

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Disabled and Archiver Appliance not Configured

|  |  |
| --- | --- |
| The following permissions are required for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability disabled. VPC, subnet and security group settings are set to (Create new) in the [archiver appliance](glacier_archiver_appliance.md) settings.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Sid": "VisualEditor0",        "Effect": "Allow",        "Action": [          "s3:DeleteObject",          "s3:PutObject",          "s3:GetObject",          "s3:RestoreObject",          "s3:ListBucket",          "s3:AbortMultipartUpload",          "s3:GetBucketVersioning",          "s3:ListAllMyBuckets",          "s3:GetBucketLocation",          "s3:GetBucketObjectLockConfiguration",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs",          "ec2:CreateVpc",          "ec2:CreateSubnet",          "ec2:DescribeAvailabilityZones",          "ec2:CreateRoute",          "ec2:CreateInternetGateway",          "ec2:AttachInternetGateway",          "ec2:ModifyVpcAttribute",          "ec2:CreateSecurityGroup",          "ec2:DeleteSecurityGroup",          "ec2:AuthorizeSecurityGroupIngress",          "ec2:AuthorizeSecurityGroupEgress",          "ec2:DescribeRouteTables",          "ec2:DescribeInstanceTypes"        ],        "Resource": "\*"      }    ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled and Archiver Appliance Configured Beforehand

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability disabled. Amazon VPC, subnet and security group settings for an archiver appliance are configured beforehand.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Sid": "VisualEditor0",        "Effect": "Allow",        "Action": [          "s3:DeleteObject",          "s3:PutObject",          "s3:GetObject",          "s3:RestoreObject",          "s3:ListBucket",          "s3:AbortMultipartUpload",          "s3:GetBucketVersioning",          "s3:ListAllMyBuckets",          "s3:GetBucketLocation",          "s3:GetBucketObjectLockConfiguration",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs"        ],        "Resource": "\*"      }    ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Immutability Enabled and Archiver Appliance not Configured

|  |  |
| --- | --- |
| The following permissions are required for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability enabled. VPC, subnet and security group settings are set to (Create new) in the [archiver appliance](glacier_archiver_appliance.md) settings.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Sid": "VisualEditor0",        "Effect": "Allow",        "Action": [          "s3:DeleteObject",          "s3:PutObject",          "s3:GetObject",          "s3:RestoreObject",          "s3:ListBucket",          "s3:AbortMultipartUpload",          "s3:GetBucketVersioning",          "s3:ListAllMyBuckets",          "s3:GetBucketLocation",          "s3:GetBucketObjectLockConfiguration",          "s3:PutObjectRetention",          "s3:GetObjectVersion",          "s3:PutObjectLegalHold",          "s3:GetObjectRetention",          "s3:DeleteObjectVersion",          "s3:ListBucketVersions",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs",          "ec2:CreateVpc",          "ec2:CreateSubnet",          "ec2:DescribeAvailabilityZones",          "ec2:CreateRoute",          "ec2:CreateInternetGateway",          "ec2:AttachInternetGateway",          "ec2:ModifyVpcAttribute",          "ec2:CreateSecurityGroup",          "ec2:DeleteSecurityGroup",          "ec2:AuthorizeSecurityGroupIngress",          "ec2:AuthorizeSecurityGroupEgress",          "ec2:DescribeRouteTables",          "ec2:DescribeInstanceTypes"        ],        "Resource": "\*"      }    ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)4. Immutability Enabled and Archiver Appliance Configured Beforehand

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability enabled. Amazon VPC, subnet and security group settings for an archiver appliance are configured beforehand.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Sid": "VisualEditor0",        "Effect": "Allow",        "Action": [          "s3:DeleteObject",          "s3:PutObject",          "s3:GetObject",          "s3:RestoreObject",          "s3:ListBucket",          "s3:AbortMultipartUpload",          "s3:GetBucketVersioning",          "s3:ListAllMyBuckets",          "s3:GetBucketLocation",          "s3:GetBucketObjectLockConfiguration",          "s3:PutObjectRetention",          "s3:GetObjectVersion",          "s3:PutObjectLegalHold",          "s3:GetObjectRetention",          "s3:DeleteObjectVersion",          "s3:ListBucketVersions",          "ec2:DescribeInstances",          "ec2:CreateKeyPair",          "ec2:DescribeKeyPairs",          "ec2:RunInstances",          "ec2:DeleteKeyPair",          "ec2:DescribeVpcAttribute",          "ec2:CreateTags",          "ec2:DescribeSubnets",          "ec2:TerminateInstances",          "ec2:DescribeSecurityGroups",          "ec2:DescribeImages",          "ec2:DescribeVpcs"        ],        "Resource": "\*"      }    ]  } | |

Read-Only Permissions for Amazon S3 and S3 Compatible Object Storage

The following permissions are required to connect to Amazon S3 or S3 Compatible object storage from a second backup server when performing data recovery operations.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Enabled

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 or S3 compatible object storage with immutability enabled.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Effect": "Allow",        "Action": [            "s3:ListBucket",            "s3:GetBucketLocation",            "s3:GetObject",            "s3:ListAllMyBuckets",            "s3:GetBucketVersioning",            "s3:GetBucketObjectLockConfiguration",            "s3:ListBucketVersions",            "s3:GetObjectVersion",            "s3:GetObjectRetention",            "s3:GetObjectLegalHold"        ],        "Resource": "\*"      }    ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 or S3 compatible object storage with immutability disabled.  |  | | --- | | {    "Version": "2012-10-17",    "Statement": [      {        "Effect": "Allow",        "Action": [            "s3:ListBucket",            "s3:GetBucketLocation",            "s3:GetObject",            "s3:ListAllMyBuckets",            "s3:GetBucketVersioning",            "s3:GetBucketObjectLockConfiguration",            "s3:CreateBucket",            "s3:DeleteBucket"        ],        "Resource": "\*"      }    ]  } | |

Batch Retrieval Permissions for Amazon S3 Glacier

The following permissions are required to perform standard accelerated retrieval that uses S3 Batch Operations:

|  |
| --- |
| "iam:GetRole",  "iam:CreateRole",  "iam:PutRolePolicy",  "iam:DeleteRolePolicy",  "iam:DeleteRole",  "iam:PassRole",  "s3:CreateJob",  "s3:DescribeJob” |

Permissions for Amazon EBS Encryption

If you have EBS encryption enabled in Amazon EC2, specific permissions are required for a helper appliance to perform a health check of backup files in object storage and run the [archiving job](archiving_job.md).

1. You must grant this permission to the IAM user.

|  |
| --- |
| "ec2:GetEbsEncryptionByDefault" |

1. You must grant the following permissions for the default encryption key to an IAM Role using a [Key Policy](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html).

|  |
| --- |
| "kms:Encrypt",  "kms:Decrypt",  "kms:ReEncrypt\*",  "kms:GenerateDataKey\*",  "kms:DescribeKey",  "kms:CreateGrant" |

Azure Archive Object Storage Permissions

The following permissions are required to use Azure Archive object storage.

|  |
| --- |
| {    "properties": {      "roleName": "CUSTOM\_ROLE\_MINIMAL\_PERMISSIONS",      "description": "CUSTOM\_ROLE\_MINIMAL\_PERMISSIONS",      "assignableScopes": [        "/subscriptions/111111-1111-1111-0000-00000000000"      ],      "permissions": [        {          "actions": [            "Microsoft.Authorization/\*/read",            "Microsoft.Compute/locations/\*",            "Microsoft.Compute/virtualMachines/\*",            "Microsoft.Compute/disks/read",            "Microsoft.Compute/disks/write",            "Microsoft.Compute/disks/delete",            "Microsoft.Network/locations/\*",            "Microsoft.Network/networkInterfaces/\*",            "Microsoft.Network/networkSecurityGroups/join/action",            "Microsoft.Network/networkSecurityGroups/read",            "Microsoft.Network/networkSecurityGroups/write",            "Microsoft.Network/networkSecurityGroups/delete",            "Microsoft.Network/publicIPAddresses/join/action",            "Microsoft.Network/publicIPAddresses/read",            "Microsoft.Network/publicIPAddresses/write",            "Microsoft.Network/publicIPAddresses/delete",            "Microsoft.Network/virtualNetworks/read",            "Microsoft.Network/virtualNetworks/write",            "Microsoft.Network/virtualNetworks/subnets/join/action",            "Microsoft.Storage/storageAccounts/listKeys/action",            "Microsoft.Storage/storageAccounts/read",            "Microsoft.Resources/deployments/\*",            "Microsoft.Resources/subscriptions/resourceGroups/read",            "Microsoft.Resources/checkResourceName/action",            "Microsoft.Resources/subscriptions/resourceGroups/write",            "Microsoft.Resources/subscriptions/locations/read"  ],          "notActions": [],          "dataActions": [],          "notDataActions": []        }      ]    }  } |

Google Cloud Object Storage Permissions

The following permissions are required to use Google Cloud Object Storage as an object storage repository.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. General Permissions to Add Google Cloud Object Storage

|  |  |
| --- | --- |
| The following permissions are required to use Google Cloud object storage.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list"  } |  Consider the following:   * The storage.buckets.list permission is not required if you specify the bucket name explicitly at the Bucket step of the [New Object Repository](adding_google_cloud_object_storage.md) wizard. * The Owner IAM role does not necessarily grant the permissions required for working with Google Cloud Storage. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Permissions to Add Google Cloud Object Storage with Immutability

|  |  |
| --- | --- |
| The following permissions are required to use Google Cloud object storage if you enable [Immutability](immutability_object_storage_repositories.md) for it.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list"   "storage.objects.setRetention"   "storage.objects.update"  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Read-Only Permissions for Google Cloud Object Storage

|  |  |
| --- | --- |
| The following permissions are required to connect to Google Cloud object storage from a second backup server when performing data recovery operations.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.get",   "storage.objects.list"  } | |

Page updated 2026-07-21

