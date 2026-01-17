---
title: "Veeam Cloud Connect Backup"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_limitations.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication has the following specifics and limitations for Veeam Cloud Connect Backup.

Backup, Backup Copy and Restore

* Veeam Backup & Replication does not support backup copy jobs if the cloud repository is used as a source backup repository. The backup copy job must use a backup repository configured locally on the tenant side as a source one.
* Veeam Backup & Replication does not support the use of backup repositories with rotated drives as cloud repositories.
* Transaction log backup is not supported for backup jobs targeted at the cloud repository. You can back up transaction logs only with backup copy jobs in the immediate copy mode.

Note that cloud repositories backed by object storage systems are not supported by transaction log backup copy jobs.

* Instant VM Recovery, multi-OS file-level restore, restore to Proxmox VE, restore to oVirt KVM, restore to Microsoft Azure and Amazon EC2 from backups in the cloud repository are not supported on the tenant side.

If Nutanix AHV Plug-in is installed and a Nutanix AHV cluster is added in Veeam Backup & Replication, the tenant can perform instant recovery to Nutanix AHV form backups that reside in the cloud repository. For more information, see the [Instant Recovery](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery.html?ver=9) section in the Veeam Backup for Nutanix AHV User Guide.

Some restore operations are available on the SP side only, including Instant Recovery from VM backups and Veeam Agent backups, restore to Microsoft Azure and restore to Amazon EC2. To learn more, see [Restoring Data from Tenant Backups](cc_data_restore.md).

* Removed GFS restore points could remain displayed in the Veeam backup console on the tenant side. To refresh the list of restore points, disable the job that created the restore points and rescan the SP in the tenant Veeam backup console.
* The Copy backup and Move backup operations to, from and between cloud repositories are not supported.
* The Forget and Remove from disk operations for restore points created by tenant backup copy jobs are unavailable in the Veeam backup console. The SP can find and remove missing restore points using Veeam PowerShell cmdlets on the SP side only. For more information, see [this Veeam KB article](https://www.veeam.com/kb3187).

* In the scenario where the SP uses backup repositories that support immutability as cloud repositories, tenant backups become immutable for the number of days specified in the backup repository settings. Veeam Backup & Replication does not delete tenant backups within a job session or by the [background retention job](cc_background_retention.md) until both the retention period and immutability period end for these backups. The tenant should be aware of the fact that because of immutability, their backups may remain in the cloud repository for the longer period than specified in the job settings.
* A machine that runs the tenant Veeam backup console must have access to the cloud gateway over the network. For example, connection to the cloud gateway is required when the tenant performs file-level restore using the backup console installed on a different machine than the tenant backup server.
* For backup copies of Proxmox VMs, Veeam Cloud Connect supports only File-Level Restore.

|  |
| --- |
| Note |
| Veeam Cloud Connect does not support NAS backup. |

File Operations

Tenants can manually copy backup files to and from the cloud repository using the Files view in the Veeam Backup & Replication console. Scheduled file copy jobs and associated backup copy jobs are not supported.

Scale-Out Backup Repositories Used as Cloud Repositories

Consider the following:

* The SP cannot expose a scale-out backup repository as a cloud repository if unlimited number of concurrent tasks is specified for at least one extent added to this scale-out backup repository.
* Tenants cannot use the Files view in the Veeam Backup & Replication console to copy backup files to and from a scale-out backup repository exposed as a cloud repository. Such cloud repositories are displayed in the tenant Veeam Backup & Replication console in the read-only mode.

Deduplicating Storage Appliances Used as Cloud Repositories

It is not recommended to use deduplicating storage appliances as cloud repositories. To protect VM data that is backed up to the cloud repository, tenants are likely to use data encryption. For deduplicating storage appliances, encrypted data blocks appear as different though they may contain duplicate data. Thus, deduplicating storage appliances will not provide the expected deduplication ratio. To learn more, see the [Data Encryption](https://helpcenter.veeam.com/docs/vbr/userguide/data_encryption.html?ver=13) section in the Veeam Backup & Replication User Guide.

If the SP uses a deduplicating storage appliance as a cloud repository, the SP must consider the following limitations.

General

To keep track of tenant quota consumption, Veeam Backup & Replication uses information about the size of backed-up data reported by a backup repository. A backup repository calculates the size of backed-up data based on the size of source data before deduplication. As a result, the actual size of tenant backup data in the cloud repository may be significantly smaller than the reported used space. The difference depends on whether the tenant uses data encryption and on the backup repository type.

This approach leads to the following consequences:

* The tenant does not gain advantage from using data deduplication other than native deduplication and compression provided by Veeam and performed within a backup job.

* Tenant backup jobs may fail to back up data to a cloud repository even in case deduplicating storage has free storage space.

To overcome this limitation, it is recommended that the SP over-provisions storage space on the deduplicating storage appliance used as a cloud repository.

Consider the following example:

* The tenant backs up VMs whose total size is 80 GB.
* The tenant quota size is 100 GB, and it is allocated on a deduplicating storage appliance used as a cloud repository.
* On deduplicating storage, tenant VM backup data consumes 30 GB.

In this case, the backup repository will display that used storage space is 80 GB, and the tenant will be able to back up additional 20 GB, and not 70 GB. To let the tenant back up the total amount of 100 GB of data, the SP needs to use over-provisioning.

Dell Data Domain

The length of forward incremental and forever forward incremental backup chains that contain one full backup and a set of subsequent incremental backups cannot be greater than 120 restore points. To overcome this limitation, the tenant can do the following:

* For backup jobs, the tenant can schedule full backups (active or synthetic) to split the backup chain into shorter series. For example, to perform backups at 15-minute intervals, 24 hours a day, the tenant must schedule synthetic full backups every day. In this scenario, intervals immediately after midnight may be skipped due to duration of synthetic processing.
* For backup copy jobs, the tenant can specify the necessary number of restore points in the backup copy job settings. The number of restore points in the backup chain must be less than 120.

If the SP plans to use Dell Data Domain as a cloud repository, it is strongly recommended that the SP informs tenants about limitations for the backup chain length.

HPE StoreOnce

Veeam Backup & Replication does not support usage of HPE StoreOnce deduplicating storage appliances as cloud repositories.

If the SP plans to use a scale-out backup repository as a cloud repository, they should consider the following limitations:

* The SP cannot add an HPE StoreOnce appliance as an extent to a scale-out repository that is used as a cloud repository.
* The SP cannot use a scale-out backup repository as a cloud repository if an HPE StoreOnce appliance is added as an extent to this scale-out backup repository.

Object Storage Repositories Used as Cloud Repositories

To learn about considerations and limitations for the backup to object storage functionality, see [Backup to Object Storage](cc_object_storage.md#consider).

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
