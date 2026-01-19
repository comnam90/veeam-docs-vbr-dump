---
title: "Access Permissions for Direct Connection to Object Storage"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_object_storage_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Access Permissions for Direct Connection to Object Storage


To back up data to object storage, you must set up access permissions. General permissions are listed in the [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#using-object-storage-repositories) section in the Veeam Backup & Replication User Guide.

Additional permissions are required for object storage in the Veeam Cloud Connect infrastructure. The list of required permissions differs depending on the selected object storage and the way the SP sets the backup infrastructure. To learn more, see the following subsections:

* [Amazon S3](#aws_s3)
* [S3 compatible storage (including IBM Cloud and Wasabi Cloud)](#s3)
* [Google Cloud](#google)

Amazon S3

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use Amazon S3 storage with immutability enabled, see permissions required for immutability in the [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#using-object-storage-repositories) section in the Veeam Backup & Replication User Guide. To learn more about immutability, see the [Backup Immutability](https://helpcenter.veeam.com/docs/vbr/userguide/agents_object_storage_backup_immutability.html?ver=13) section in the Veeam Backup & Replication User Guide.

The list of permissions below is required for the following configuration:

* You plan to back up data to the Amazon S3 storage.
* You selected direct connection in the object storage settings. To learn more, see the [Adding Amazon S3 Object Storage, Amazon S3 Glacier Storage and AWS Snowball Edge](https://helpcenter.veeam.com/docs/vbr/userguide/adding_amazon_object_storage.html?ver=13) section in the Veeam Backup & Replication User Guide.

If you plan to back up data using the configuration above, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| {   "iam:CreateAccessKey",   "iam:CreatePolicy",   "iam:CreatePolicyVersion",   "iam:CreateUser",   "iam:DeleteAccessKey",   "iam:DeletePolicy",   "iam:DeletePolicyVersion",   "iam:DeleteUser",   "iam:DeleteUserPolicy",   "iam:DetachUserPolicy",   "iam:GetPolicy",   "iam:GetPolicyVersion",   "iam:GetUser",   "iam:GetUserPolicy",   "iam:ListAccessKeys",   "iam:ListAttachedUserPolicies",   "iam:ListPolicyVersions",   "iam:ListUserPolicies",   "iam:PutUserPolicy",   "iam:SetDefaultPolicyVersion",   "iam:SimulatePrincipalPolicy",   "iam:TagUser" |

S3 Compatible Storage (Including IBM Cloud, Wasabi Cloud)

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use S3 Compatible storage with immutability enabled, see permissions required for immutability in the [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#s3compatible) section in the Veeam Backup & Replication User Guide. To learn more about immutability, see the [Backup Immutability](https://helpcenter.veeam.com/docs/vbr/userguide/agents_object_storage_backup_immutability.html?ver=13) section in the Veeam Backup & Replication User Guide.

The list of permissions below is required for the following configuration:

* You plan to back up data to the S3 compatible storage.
* Direct connection is selected in the object storage settings. To learn more, see the [Specify Object Storage Account](https://helpcenter.veeam.com/docs/vbr/userguide/compatible_repository_account.html?ver=13) section in the Veeam Backup & Replication User Guide.

* The Provided by IAM/STS object storage capabilities option is selected for the object storage. To learn more, see the [Managing Permissions for S3 Compatible Object Storage](https://helpcenter.veeam.com/docs/vbr/userguide/access_permissions.html?ver=13#managing-permissions-for-s3-compatible-object-storage) section in the Veeam Backup & Replication User Guide.

If you plan to back up data using the configuration above, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| {  "iam:AttachUserPolicy",   "iam:CreateAccessKey",   "iam:CreatePolicy",   "iam:CreatePolicyVersion",   "iam:CreateUser",   "iam:DeleteAccessKey",   "iam:DeletePolicy",   "iam:DeletePolicyVersion",   "iam:DeleteUser",   "iam:DeleteUserPolicy",   "iam:DetachUserPolicy",   "iam:GetPolicy",   "iam:GetPolicyVersion",   "iam:GetUser",   "iam:GetUserPolicy",   "iam:ListAccessKeys",   "iam:ListAttachedUserPolicies",   "iam:ListPolicyVersions",   "iam:ListUserPolicies",   "iam:PutUserPolicy",   "iam:SetDefaultPolicyVersion",   "sts:GetCallerIdentity" } |

Google Cloud

The list of permissions below is required for the following configuration:

* You plan to back up data to the Google Cloud storage.
* You configured Helper Appliance in the object storage settings. To learn more, see the [Configuring Helper Appliance](https://helpcenter.veeam.com/docs/vbr/userguide/google_cloud_storage_mount_server.html?ver=13#configuring-helper-appliance) section in the Veeam Backup & Replication User Guide.
* You selected direct connection in the object storage settings. To learn more, see the [Specify Object Storage Account](https://helpcenter.veeam.com/docs/vbr/userguide/google_cloud_repository_account.html?ver=13) section in the Veeam Backup & Replication User Guide.

If you plan to back up data using the configuration above, make sure the user account that you specify in the Helper Appliance settings has the following permissions:

|  |
| --- |
| {   "iam.serviceAccounts.create",   "iam.serviceAccounts.delete",   "iam.serviceAccounts.get",   "iam.serviceAccounts.list",   "storage.buckets.get",   "storage.buckets.getIamPolicy",   "storage.buckets.list",   "storage.buckets.setIamPolicy",   "storage.buckets.update",   "storage.hmacKeys.create",   "storage.hmacKeys.delete",   "storage.hmacKeys.get",   "storage.hmacKeys.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list" } |


