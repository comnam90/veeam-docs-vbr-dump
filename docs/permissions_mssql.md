---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_mssql.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

For general requirements for permissions that must be provided to the user account to install and work with Veeam Backup & Replication, see [Permissions](required_permissions.md) for Veeam Backup & Replication. In addition to general port requirements, make sure that user accounts have permissions listed in the following subsections:

* [Permissions for Veeam Plug-In](#vp)
* [Permissions for Object Storage](#object)

Permissions for Veeam Plug-In

| Operation | Required Roles and Permissions |
| --- | --- |
| Installing and updating Veeam Plug-In | The account used for installing and updating Veeam Plug-In must be a member of the local Administrators group. Local administrator permissions are required to install and manage Veeam Plug-In Toolbar in Microsoft SQL Server Management Studio. |
| Performing backup and restore operations in Veeam Plug-In | To be able to connect to the SQL instance, the account used for starting Microsoft SQL Server backup and restore processes must meet the following conditions:   * The account must be added to the following roles: public, sysadmin.  * If the account is not a member of the Administrators group, you must enable the Create Global Objects security policy for the account. For detailed instructions on how to manage the Create Global Objects security policy, see [this Microsoft article](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/create-global-objects). |
| Connecting to Veeam Backup & Replication, managing backups | The account that is used to authenticate against Veeam Backup & Replication must have access permissions on required Veeam backup repository servers. To learn how to configure permissions on repositories, see [Access and Encryption Settings on Backup Repositories](repository_permissions_mssql.md).  Veeam Plug-In for Microsoft SQL Server uses Windows authentication methods of the Veeam Backup & Replication server to establish a connection to this server and to the backup target. It is recommended to create one user for each standalone Microsoft SQL Server or failover cluster with Veeam Plug-In.  To work with backups created by Veeam Plug-In, you can use only the same account that was used for creating the backup. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account. For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md). Alternatively, you can delete backups from the backup repository and re-create the backup using another account. For details on how to delete backups, see [Force Deleting Backups](plugins_mssql_retention_force.md) or [Deleting Backup with Veeam Backup & Replication](delete_backups_mssql.md). |

Permissions for Object Storage

The general permissions for backup to object storage are listed in [Using Object Storage Repositories](required_permissions.md#using-object-storage-repositories). Additional permissions are required if you want to back up databases with Veeam Plug-In. The list of additional permissions differs depending on the selected object storage and the way you set your backup infrastructure:

* [Amazon S3](#aws_s3)
* [S3 compatible (including IBM Cloud Object Storage and Wasabi Cloud Storage)](#s3)
* [Google Cloud Storage](#google)

Amazon S3

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use Amazon S3 storage with immutability enabled, see permissions required for immutability in [Using Object Storage Repositories](required_permissions.md#using-object-storage-repositories). For details about immutability, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the Amazon S3 storage.
* You selected direct connection in the object storage settings. For details, see [Adding Amazon S3 Object Storage](adding_amazon_object_storage.md).

If you plan to back up data using such infrastructure configuration, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| { |

S3 Compatible (Including IBM Cloud Object Storage, Wasabi Cloud Storage)

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use Amazon S3 storage with immutability enabled, see permissions required for immutability in [Using Object Storage Repositories](required_permissions.md#using-object-storage-repositories) . For details about immutability, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the S3 compatible storage.
* Direct connection is selected in the object storage settings. For details, see [Specify Object Storage Account](compatible_repository_account.md).

* The Provided by IAM/STS object storage capabilities option is selected for the object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md#managing-permissions-for-s3-compatible-object-storage).

If you plan to back up data using such infrastructure configuration, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| {   "iam:AttachUserPolicy",   "iam:CreateAccessKey",   "iam:CreatePolicy",   "iam:CreatePolicyVersion",   "iam:CreateUser",   "iam:DeleteAccessKey",   "iam:DeletePolicy",   "iam:DeletePolicyVersion",   "iam:DeleteUser",   "iam:DeleteUserPolicy",   "iam:DetachUserPolicy",   "iam:GetPolicy",   "iam:GetPolicyVersion",   "iam:GetUser",   "iam:GetUserPolicy",   "iam:ListAccessKeys",   "iam:ListAttachedUserPolicies",   "iam:ListPolicyVersions",   "iam:ListUserPolicies",   "iam:PutUserPolicy",   "iam:SetDefaultPolicyVersion",   "sts:GetCallerIdentity" } |

Google Cloud Storage

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the Google Cloud storage.
* You configured Helper Appliance in the object storage settings. For details, see [Configuring Helper Appliance](google_cloud_storage_mount_server.md#configuring-helper-appliance).
* You selected direct connection in the object storage settings. For details, see [Specify Object Storage Account](google_cloud_repository_account.md).

If you plan to back up data using such infrastructure configuration, make sure the user account that you specify in the Helper Appliance settings has the following permissions:

|  |
| --- |
| {   "iam.serviceAccounts.create",   "iam.serviceAccounts.delete",   "iam.serviceAccounts.get",   "iam.serviceAccounts.list",   "storage.buckets.get",   "storage.buckets.getIamPolicy",   "storage.buckets.list",   "storage.buckets.setIamPolicy",   "storage.buckets.update",   "storage.hmacKeys.create",   "storage.hmacKeys.delete",   "storage.hmacKeys.get",   "storage.hmacKeys.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list" } |

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
