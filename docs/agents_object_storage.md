---
title: "Backup to Object Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_object_storage.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Backup to Object Storage


If you want to store your data in a cloud-based or on-premises object storage, you can create Veeam Agent backups in an object storage repository.

The following Veeam Agents support the object storage as a primary repository for backup jobs, backup policies, and backup copy jobs:

* Veeam Agent for Microsoft Windows
* Veeam Agent for Linux
* Veeam Agent for Mac
* Veeam Agent for Unix (with [limitations](#unix))

You can store Veeam Agent backups in the following types of object storage:

* Amazon S3
* S3 compatible
* Google Cloud Storage
* Microsoft Azure Blob Storage
* IBM Cloud Object Storage
* Wasabi Cloud Storage
* Veeam Data Cloud Vault
* 11:11 Cloud Object Storage

Veeam Agents communicate with the object storage using one of the following connection modes:

* Connection through a gateway server. With this connection mode, Veeam Agents access object storage through Veeam Backup & Replication. As a result, Veeam Agent access to object storage is managed by a proxy component — a gateway server assigned in the Veeam Backup & Replication console. Backup data is sent from Veeam Agent computer to the gateway server, then it is sent from gateway server to the object storage.
* Direct connection. With this connection mode, Veeam Agents access object storage directly. Backup data is sent from Veeam Agent computer to the object storage. Veeam Agent access to object storage is managed by Application Programming Interface (API) provided by an external cloud service provider. To learn more, see [Access Permissions for Direct Connection to Object Storage](agents_object_storage_direct_access.md).

If you plan to back up to the repository in the object storage in the direct connection mode and a backup job managed by Veeam Agent, keep in mind that Veeam Agents will still connect to Veeam Backup & Replication periodically. Using these connections, Veeam Agent will update license and backup job settings. These connections are not necessary for backup job sessions.

|  |
| --- |
| IMPORTANT |
| * After you switch your repository from one connection mode to another, Veeam Agent will need to connect to Veeam Backup & Replication to update repository settings. Until this connection is made, all backup operations by Veeam Agents will fail.  * If you plan to back up data to the S3 compatible storage in the direct connection mode, you must perform an extra step: manually set access to the object storage for Veeam Agents. To learn more, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md). * Veeam Agent always performs backup of cloud machines directly to the cloud regardless of the connection mode specified in the backup repository settings. |

Getting Started

To back up Veeam Agent computer data to an object storage, you must complete the following steps:

1. Add repository in the Veeam backup console. To learn more, see [Adding Object Storage Repositories](new_object_storage.md).

You can use an object storage in Veeam Backup & Replication as one of the following repositories:

* Backup repository. To learn more, see [Backup Repositories](backup_repository.md).
* Scale-out backup repository added as a Veeam backup repository. To learn more, see [Scale-Out Backup Repositories](backup_repository_sobr.md).
* Cloud repository. To learn more, see the [Backup to Object Storage](https://helpcenter.veeam.com/docs/backup/cloud/cc_object_storage.html?ver=120) section in the Veeam Cloud Connect Guide.

1. [For S3 compatible object storage] Set access to the added S3 compatible object storage. To learn more see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).
2. Create a Veeam Agent backup job or policy and specify the following repository as a target location for backup files:

* If the object storage is configured as a backup repository or a scale-out backup repository in your infrastructure, specify a Veeam backup repository as a target location for backup files, then select the repository from the list of available repositories.
* If the object storage is provided to you by Service Provider, specify a Veeam Cloud Connect repository as a target location for backup files, then select the repository from the list of available repositories.

To learn more, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).

Considerations and Limitations

Before you configure your backup infrastructure to enable backup to object storage, consider the following:

* You cannot back up data using Veeam Agent backup job or policy to the following storage devices:

* AWS SnowBall
* Azure Databox

* Data in object storage repositories must be managed solely by Veeam Backup & Replication, including retention and data management. Lifecycle rules are not supported, and their enabling may result in backup and restore failures.
* For backups located in object storage repositories, synthetic full backup is not supported.
* For backups located in object storage repositories, compact full backup file option is not supported.
* For backups located in object storage repositories, data recovery options are not available if you access the object storage repository using credentials with the read-only access permissions.
* If you plan to add more than one repository in the object storage as a performance tier of a scale-out backup repository and you plan to back up to these repositories using a [direct connection](#direct), you can use only managed by backup server backup jobs. If you want to back up data to a scale-out backup repository with backup jobs managed by Veeam Agent, you can use only scale-out backup repositories that have only one repository in the object storage in the direct connection mode as a performance tier.
* If Veeam Backup & Replication uses [HTTP or HTTPS proxies](hmc_configure_proxies.md), backup to object storage is only available through a gateway server.
* [For backup jobs managed by Veeam Agent] If you have a backup job targeted at an object storage added as an extent of a scale-out backup repository in the [direct connection mode](#direct) and you put this extent to the Maintenance or Seal mode during the backup job session while there is no connection between Veeam Backup & Replication and the object storage, the current and subsequent backup job sessions will end successfully.

To learn about modes you can put extents of scale-out backup repositories to, see [Service Actions with Scale-Out Backup Repositories](backup_repository_sobr_service.md).

* [For backup jobs managed by Veeam Agent] You cannot back up data to the Veeam Data Cloud Vault storage added in the [direct connection mode](#direct).
* [For backup jobs managed by Veeam Agent] If you back up data to the S3 compatible object storage with multiple buckets, Veeam Agent will ignore the number of workloads set for one bucket and will store all backups in a single child bucket. To learn more about multiple buckets, see [Multiple Buckets for S3 Compatible Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_repository.html?ver=13#multiple-buckets-for-s3-compatible-object-storage-repositories).

* [For Unix-based Veeam Agent computers] Consider the following:

* Veeam Agent for Unix supports only Amazon S3, as well as selected types of S3 compatible storage: MinIO, IBM Cloud and Wasabi Cloud.
* Veeam Agent for Unix does not support backup to object storage for computers added to a protection group for pre-installed Veeam Agents
* [For Oracle Solaris 10 1/13] To enable Veeam Agent connection to S3 compatible storage repositories, you must install the necessary CA certificates. For more information on installing the certificates, see [this Veeam KB article](https://veeam.com/kb4735).
* Veeam Agent for Unix only supports backup repositories that are configured to have [direct connection](#direct) to object storage.

* For Microsoft Azure Blob storage, Veeam Agents do not support soft delete for blobs.
* If you plan to back up data to the Microsoft Azure Blob storage using a [direct connection](#direct), the following limitations apply:

* Cool tier is not supported for the following configurations:

* Backup policies targeted at the object storage added as the Veeam backup repository.
* Backup jobs and policies targeted at the object storage added as cloud repository.

To learn more about access tiers for blob data, see [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview).

* Immutability is not supported for the following configurations:

* Backup policies targeted at the object storage added as the Veeam backup repository.
* Backup jobs and policies targeted at the object storage added as cloud repository.

To learn more about immutability, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).

* Veeam Agents do not support direct backup under the general-purpose V1 storage account type.


