---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_plan_and_manage_permissions.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Permissions


For general requirements for permissions that must be provided to the user account to install and work with Veeam Backup & Replication, see [Permissions](required_permissions.md) for Veeam Backup & Replication. In addition to general requirements, make sure that user accounts have the following permissions:

* [Permissions for MongoDB Replica Set](#backup)
* [Permissions for Object Storage](#obj_stor)

Permissions for MongoDB Replica Set

| Operation | Required Roles and Permissions |
| --- | --- |
| Connecting to the MongoDB replica set, discovering MongoDB nodes | To connect to the MongoDB replica set, your credentials must meet the following requirements:   * The account must be able to authenticate against MongoDB admin database. * The account must have the the following roles:  * ClusterMonitor role to collect information about replica sets.  * Backup role to perform backup operations.  * HostManager role to lock nodes during backup operations.   To learn more about these roles, see [MongoDB documentation](https://www.mongodb.com/docs/manual/reference/built-in-roles/).   * If you want to use TLS with your credentials, you must use client certificate that meet requirements by MongoDB. For details, see [MongoDB documentation](https://www.mongodb.com/docs/manual/core/security-x.509/).   To learn more about TLS support by MongoDB, see [MongoDB documentation](https://www.mongodb.com/docs/manual/tutorial/configure-ssl/).  For details, see [Specify Deployments](mongo_protection_group_scope_deployments.md). |
| Connecting to MongoDB nodes, installing and updating Veeam components | The account specified in the protection group configuration settings to connect to MongoDB nodes must have the following permissions:   * The account must have root privileges.  * The account must be able to authenticate against the Veeam Backup & Replication server.   For enhanced security, we recommend creating a separate standard user that will be solely dedicated to performing the backup and restore operations.  For details, see [Specify Computers](mongo_protection_group_scope_computers.md). |
| Restoring MongoDB data | To restore MongoDB data using Veeam Explorer for MongoDB, consider the required permissions in [Permissions](https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_permissions.html?ver=13). |

Permissions for Object Storage

The general permissions for backup to object storage are listed in [Using Object Storage Repositories](required_permissions.md#using-object-storage-repositories). Additional permissions are required if you want to use MongoDB Backup. The list of additional permissions differs depending on the selected object storage and the way you set your backup infrastructure:

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


