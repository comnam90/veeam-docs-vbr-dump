---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_before_you_begin.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

This section contains information that you should consider before you create an object storage backup job.

General Considerations

Before you create an object storage backup job, consider the following:

* Consider limitations listed in the [Supported Platforms, Applications and Workloads](platform_support.md#os) section.
* The account that you use to add Amazon S3 and S3 Compatible object storage as unstructured sources and back up data from them must be able to perform the actions listed in the [Permissions](required_permissions.md#os_unstructured) section.
* Backup infrastructure components that will take part in the object storage backup process must be added to the backup infrastructure and properly configured. These include objects storage sources to back up, backup proxies, and all repositories, including cache, backup, archive, and secondary repositories. For more information, see the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md) section.
* The target backup repository must have enough free space to store created backup files. If you want to receive notifications on the repository running low on free space, configure global notification settings as described in the [Specifying Global Notification Settings](global_notifications.md) section.
* Make sure that repositories intended to store object storage backups are not configured to store files in the Write Once Read Many (WORM) status. Otherwise, the backup jobs will fail when Veeam Backup & Replication cannot update the backup metadata files.
* If you plan to map an object storage backup job to a backup that already exists in the backup repository, you must perform the rescan operation for this backup repository. Otherwise, Veeam Backup & Replication will not be able to recognize backup files in the backup repository.

For more information on how to rescan backup repositories, see the [Rescanning Backup Repositories](rescanning_backup_repositories.md) section.

* Antivirus software may significantly slow down object storage backup jobs. To improve performance, we recommend you exclude the c:\Program Files (x86)\Veeam\Backup Transport\x64\VeeamAgent.exe process from the antivirus scan on machines running the object storage backup proxy and backup repository roles. Keep in mind that it can weaken the security of these machines.
* If the object content and modification time are not changed, Veeam Backup & Replication will back up only attributes of this object.
* Veeam Backup & Replication does not back up version history of objects.

* Veeam Backup & Replication does not create the separate node in the inventory pane for the archived backups. If you plan to use archive repositories and want to make sure that backups were moved to it, you can do it using backup properties. For more information, see [Viewing Unstructured Data Backup Properties](unstructured_data_backup_view_properties.md).
* You cannot use the capacity tier of [scale-out backup repositories](backup_repository_sobr.md) as a target for object storage backup jobs.

* If you plan to use pre-job and post-job scripts, you must create scripts before you configure the object storage backup job.

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

Limitations for Microsoft Azure Blob Storage

Before you create an object storage backup job, consider the following limitations for Microsoft Azure Blob storage:

* Veeam Backup & Replication backs up objects encrypted only with Microsoft-managed and customer-managed keys. If you create a blob using the [Put Blob](https://learn.microsoft.com/en-us/rest/api/storageservices/put-blob) or [Put Block List](https://learn.microsoft.com/en-us/rest/api/storageservices/put-block-list) API method and specify a customer-provided key, Veeam Backup & Replication cannot back up such blobs. For more information about customer-provided keys, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/storage/blobs/encryption-customer-provided-keys).

* Veeam Backup & Replication does not support backup of the objects with the archive access tier.

* Veeam Backup & Replication does not support the following backup options if you add the source Microsoft Azure Blob storage using the [Microsoft Azure storage account with Microsoft Entra authorization](azure_entra_id.md):

* Backup of ACL for Azure containers.
* Backup of hierarchical namespace.

Limitations for Amazon S3 Storage

Before you create an object storage backup job, consider the following limitations for Amazon S3 storage:

* Veeam Backup & Replication backs up objects encrypted only with Amazon S3 managed keys and AWS KMS keys. If you add an object to a bucket using the [Put Object](https://docs.aws.amazon.com/AmazonS3/latest/API/API_PutObject.html) API method and specify a customer-provided key, Veeam Backup & Replication cannot back up such objects. For more information about customer-provided keys, see [this Amazon article](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ServerSideEncryptionCustomerKeys.html).

* Veeam Backup & Replication does not support backup of the objects with the Amazon S3 Glacier Flexible Retrieval and Amazon S3 Glacier Deep Archive storage classes.

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
