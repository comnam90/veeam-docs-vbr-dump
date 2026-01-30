---
title: "Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Backup Repositories


A backup repository is a storage location where Veeam keeps backup files, VM copies and metadata for replicated VMs.

|  |
| --- |
| Note |
| Consider the following:   * Do not configure multiple backup repositories pointing to the same location or using the same path. * Do not configure multiple backup repositories with "nested" paths (when one repository path is a sub-path of another repository), for example:   /mnt/repo/backups/  /mnt/repo/backups/production/ |

You can use the following storage types as backup repositories:

* Direct attached storage. You can add virtual and physical servers as backup repositories:

* [Microsoft Windows server](ms_server.md)
* [Linux server](linux_server.md)
* [Hardened Repository](hardened_repository.md)

* Network attached storage. You can add the following network shares as backup repositories:

* [SMB (CIFS) share](smb_share.md)
* [NFS share](nfs_share.md)

* Deduplicating storage appliances. You can add the following deduplicating storage appliances as backup repositories:

* [Dell Data Domain](dell_dd.md)
* [ExaGrid](deduplicating_appliance_exgrid.md)
* [Fujitsu ETERNUS CS800](fujitsu.md)
* [HPE StoreOnce](deduplicating_appliance_storeonce.md)
* [Infinidat InfiniGuard](infinidat_infiniguard.md)
* [Quantum DXi](deduplicating_appliance_quantum.md)

* Object storage. You can add the following object storage solutions as backup repositories:

* [Veeam Data Cloud Vault](osr_adding_veeam_data_cloud_vault.md)
* [Amazon S3, Amazon S3 Glacier and AWS Snowball Edge](adding_amazon_object_storage.md)
* [S3 compatible, S3 compatible with data archiving](adding_s3c_object_storage.md)
* [Google Cloud](adding_google_cloud_object_storage.md)
* [Microsoft Azure Blob, Azure Archive Storage and Azure Data Box](adding_azure_object_storage.md)
* [IBM Cloud](adding_ibm_object_storage.md)
* [Wasabi Cloud Storage](adding_wasabi_object_storage.md)
* [11:11 Cloud Object Storage](adding_1111.md)

* External repositories. For more information, see [External Repositories](external_repository.md).

In This Section

* [Microsoft Windows Server](ms_server.md)
* [Linux Server](linux_server.md)
* [Hardened Repository](hardened_repository.md)
* [SMB (CIFS) Share](smb_share.md)
* [NFS Share](nfs_share.md)
* [Deduplicating Storage Appliances](deduplicating_storage_appliances.md)

* [Backup Repositories with Rotated Drives](backup_repository_rotated.md)
* [Object Storage Repositories](object_storage_repository.md)
* [External Repositories](external_repository.md)

* [Managing Backup Repositories](managing_backup_repository_data.md)

Related Topics

[Scale-Out Backup Repositories](backup_repository_sobr.md)


