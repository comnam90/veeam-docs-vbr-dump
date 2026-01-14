---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_preparation_permissions.html"
last_updated: "11/18/2025"
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
| Installing and updaing Veeam Plug-In | The account used for installing and updating Veeam Plug-In must have root privileges. |
| Performing backup and restore operations in Veeam Plug-In | The account used to start SAP MaxDB Database Manager backup and restore operations must have access to all required files and folders. For details, see [Configuring Environment](plugins_sap_maxdb_deploy_configure.md). |
| Connecting to Veeam Backup & Replication, managing backups | * The account specified in the Veeam Plug-In configuration settings must be able to authenticate against the Veeam Backup & Replication server. For details, see [Configuring Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_deploy_configure_vp.md).  * The account specified in the Veeam Plug-In configuration settings must be granted access rights on the Veeam backup repository where you want to store backups.   To learn how to grant permissions on Veeam repositories, see [Access and Encryption Settings on Repositories](plugins_sap_maxdb_deploy_repo_permissions.md).   * You can work with backups created by Veeam Plug-In only with the account used for creating the backups. If you want to use another account, see required permissions in [Configuring Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_deploy_configure_vp.md). |

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

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
