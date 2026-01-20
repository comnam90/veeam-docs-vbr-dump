---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_plugin_permissions.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Permissions


For general requirements for permissions that must be provided to the user account to install and work with Veeam Backup & Replication, see [Permissions](required_permissions.md) for Veeam Backup & Replication. In addition to general port requirements, make sure that user accounts have permissions listed in the following subsections:

* [Permissions for Veeam Plug-In](#vp)
* [Permissions for Object Storage](#object)

|  |
| --- |
| Note |
| If you plan to restore Oracle databases using Veeam Explorer for Oracle, consider the required permissions listed in [Permissions](https://helpcenter.veeam.com/docs/vbr/userguide/veo_permissions.html?ver=13). |

Permissions for Veeam Plug-In

| Operation | Required Roles and Permissions |
| --- | --- |
| Configuring Veeam Plug-In | The OS user account used for configuring Veeam Plug-In must have the following permissions.   * For Linux and Unix:   To configure Veeam Plug-In on a Linux or Unix machine, use an account which is a member of the OSDBA (typically called as “dba”) group and has SYSDBA privileges.   * For Microsoft Windows:   To configure Veeam Plug-In on a Microsoft Windows machine, use an account which is a member of the ORA\_DBA group and has SYSDBA privileges. |
| Performing backup and restore in Veeam Plug-In | The database account used for starting Oracle RMAN backup and restore processes must have the following permissions:   * To launch RMAN backup or restore, you can use any user account that has required set of privileges for backup operations on the Oracle side. Starting from Oracle Database 12c, Oracle recommends to use the SYSBACKUP role. For details, see [this Oracle article](https://docs.oracle.com/database/121/DBSEG/authorization.htm#DBSEG331).  * For Linux and Unix:   During the backup process, Veeam Plug-In connects to the database to get database properties. Thus, Linux/Unix user that started the RMAN client must be a member of the OSDBA (typically called as “dba”) group and has SYSDBA privileges.  IMPORTANT: In case you use the operating system authentication method, if you use the CONNECT command in the RMAN script, the plug-in manager process will be started by the owner of the Oracle listener, not by the user that started the RMAN client. Thus, if the listener is owned by a cluster service user (grid) that is not a member of the OSDBA group and does not have SYSDBA privileges, the plug-in manager will not be able to collect database properties and the backup will fail. As a workaround, you can add DBA privileges to the grid user.  The workaround is not required in case you use the database authentication method. For details about authentication methods, see [Authentication Against Database](rman_auth_methods.md).   * For Microsoft Windows:   During the backup process, Veeam Plug-In connects to the database to get database properties. Thus, the Oracle home user must be a member of the ORA\_DBA group and the OS authentication must be enabled for this user. |
| Connecting to Veeam Backup & Replication, managing backups | The account which is used to authenticate against Veeam Backup & Replication must have access permissions on required Veeam repository servers. To learn how to configure permissions on repositories, see [Access and Encryption Settings on Repositories](repository_permissions_rman.md).  To work with backups created by Veeam Plug-In, you can use only the account used for creating the backup. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account. For details on how to assign Veeam Backup & Replication roles, see the [Managing Users and Roles](users_roles.md). |

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


