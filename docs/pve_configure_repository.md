---
title: "Configuring Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_configure_repository.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Configuring Backup Repositories


A backup repository is a storage location where Veeam Backup & Replication keeps backup files. By default, the backup server performs the role of a backup repository. To keep your backups in another storage location, you can configure the following types of repositories:

* Direct attached storage: [Microsoft Windows](ms_server.md) and [Linux](linux_server.md) virtual and physical machines. [Hardened repositories](hardened_repository.md) based on Linux servers are also supported.
* Network attached storage: [CIFS (SMB) shares](smb_share.md) and [NFS shares](nfs_share.md).
* Deduplicating storage appliances: [ExaGrid](deduplicating_appliance_exgrid.md), [Quantum DXi](deduplicating_appliance_quantum.md), [Dell Data Domain](dell_dd.md), [HPE StoreOnce](deduplicating_appliance_storeonce.md), [Fujitsu ETERNUS](fujitsu.md), [Infinidat InfiniGuard](infinidat_infiniguard.md).

* Cloud object storage: [11:11 Cloud Object Storage, Amazon S3, S3 compatible, Google Cloud, Wasabi Cloud Storage, Veeam Data Cloud Vault, IBM Cloud and Microsoft Azure Blob](object_storage_repository.md).

To combine repositories of different types in one repository, you can configure a [scale-out backup repository](backup_repository_sobr.md) and add any of supported repositories to its [performance tier](backup_repository_sobr_extents.md).

For Linux server, Microsoft Windows server, SMB share, ExaGrid, Quantum DXi, Fujitsu ETERNUS and Infinidat InfiniGuard repositories, you can enable the Fast Clone technology that increases the speed of synthetic backup creation and transformation, reduces disk space requirements and decreases the load on storage devices. With this technology, Veeam Backup & Replication references existing data blocks on volumes instead of copying data blocks between files. Data blocks are copied only when files are modified. To learn how to configure a repository to enable this functionality, see [Fast Clone](backup_repository_block_cloning.md).

|  |
| --- |
| Important |
| Veeam Plug-in for Proxmox VE does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) and [HPE Cloud Bank Storage](storeonce_supported_features.md) repositories. However, you can use them for [storing copies of backups](pve_backups_copy.md) created with Veeam Plug-in for Proxmox VE. |


