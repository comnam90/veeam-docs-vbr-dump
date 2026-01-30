---
title: "Access Permissions for Direct Connection to Object Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_object_storage_direct_access.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Access Permissions for Direct Connection to Object Storage


If you back up data using a direct connection between the Veeam Agent computer and the object storage, access to the object storage will be managed by an API provided by this object storage. Depending on the selected object storage, access permissions are distributed differently. As a result, you must consider different limitations for the following types of object storage:

* [Amazon S3](#aws)
* [Google Cloud Storage](#google)
* [Microsoft Azure Blob Storage](#Azure)
* [Veeam Data Cloud Vault](#vault)
* [IBM Cloud, Wasabi Cloud or other S3 compatible storage](#S3)

|  |
| --- |
| NOTE |
| Backup policies cannot back up data to the Microsoft Azure Blob storage with immutability enabled and Veeam Data Cloud Vault storage added in the direct connection mode. |

Amazon S3

On the Amazon S3 storage side, Veeam Agent backup is performed with the following steps:

1. Depending on the backup job mode and the way you added the object storage to your infrastructure, Veeam Backup & Replication performs a certain operation to grant access to the repository in the object storage.

For backup jobs targeted at the Veeam backup repository

* For the following job configurations, Veeam Backup & Replication provides Veeam Agents access to the object storage repository using credentials that were specified during the repository configuration:

* Backup job managed by the backup server
* Backup policy targeted at the object storage though a gateway

* For the backup policy directly targeted at an object storage repository, Veeam Backup & Replication creates a user in AWS for each Veeam Agent that performs backups to AWS.

For backup jobs targeted at the Cloud Connect repository

* For the following job configurations, Veeam Backup & Replication creates a user in AWS for each tenant:

* Backup job managed by the backup server

* Backup policy targeted at the object storage though a gateway

* For the backup policy targeted at the object storage directly, Veeam Backup & Replication creates a user in AWS for each subtenant.

To learn more about tenants and subtenants, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120).

1. If applicable, Veeam Backup & Replication assigns a policy to each created user. This policy contains access permissions and allows Veeam Agent access only those backups that were made only by this Veeam Agent.

Keep in mind the following limitations and prerequisites:

* By default, Veeam Backup & Replication assigns an inline policy to the user. All inline policies combined cannot be greater than 2048 symbols. If you reach this limit, Veeam Backup & Replication starts assigning managed policies. All managed policies combined cannot be greater than 6144 symbols. If you reach this limit, refer to the AWS customer support.
* AWS allows to create 1500 managed policies per the AWS account. If you need more policies, refer to the AWS customer support.
* AWS allows to create 5000 users per the AWS account. If you need more users, use another AWS account.
* Consider that user accounts that you use to connect to the Amazon S3 storage have the required permissions. To learn more, see [Permissions](agents_permissions.md#aws_s3).

Google Cloud Storage

On the Google storage side, Veeam Agent backup is performed with the following steps:

1. Depending on the backup job mode and the way you added the object storage to your infrastructure, Veeam Backup & Replication performs a certain operation to grant access to the repository in the object storage.

For backup jobs targeted at the Veeam backup repository

* For the following job configurations, Veeam Backup & Replication provides Veeam Agents an access to the repository in the object storage using credentials that were specified during the repository configuration:

* Backup job managed by the backup server
* Backup policy targeted at the object storage though a gateway

* For the backup policy targeted at the object storage directly, Veeam Backup & Replication creates a user for each Veeam Agent that backs up to Google storage.

For backup jobs targeted at the Cloud Connect repository

* For the following job configurations, Veeam Backup & Replication creates a user in Google Cloud for each tenant:

* Backup job managed by backup server

* Backup policy targeted at the object storage though a gateway

* For the backup policy targeted at the object storage directly, Veeam Backup & Replication creates a user in Google Cloud for each subtenant.

To learn more about tenants and subtenants, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120).

1. If applicable, Veeam Backup & Replication assigns a policy to each bucket. This policy contains access permissions and allows Veeam Agent access only those backups that were made only by this Veeam Agent.

Keep in mind the following limitations and prerequisites:

* Policies for buckets have a size limit. If you need to increase the limit, refer to the Google customer support.
* Keep in mind that Google allows to create 100 users per the Google account. If you need more users, refer to the Google customer support.
* If you plan to target Veeam Agent backups at the Google Cloud storage using a backup policy, you must configure a Helper Appliance. To learn more, see [Configuring Helper Appliance](google_cloud_storage_mount_server.md).

* Consider that user accounts that you use to connect to the Google Cloud storage have the required permissions. To learn more, see [Permissions](agents_permissions.md#google).

Microsoft Azure Blob Storage

Access permissions are granted to Veeam Agents using shared access signatures (SAS).

Veeam Data Cloud Vault

Necessary access permissions are granted by default and cannot be modified.

IBM Cloud, Wasabi Cloud or Other S3 Compatible Storage

Keep in mind the following limitations and prerequisites:

* After you added the S3 compatible object storage, you must configure access permissions manually in the Veeam Backup & Replication console. If you selected the Provided by IAM/STS object storage capabilities option for the object storage, Veeam Backup & Replication will perform the backup operation in the same way as for the [Amazon S3 storage](#aws).

To learn more, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).

* User accounts that you use to connect to the S3 compatible storage have the required permissions. To learn more, see [Permissions](agents_permissions.md#s3).


