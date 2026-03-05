---
title: "Configuring Log and Cache Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_configure_repo.html"
last_updated: "3/3/2026"
product_version: "13.0.1.1071"
---

# Configuring Log and Cache Repositories


To protect Microsoft Entra ID tenant data and logs, you require the following repositories:

* Cache repository that stores temporary cache files for log processing.
* Primary log backup repository.
* [Optional] Secondary backup repository that stores copies of backups.

By default, the backup server can perform the roles of cache and primary log backup repositories.

You can also configure other types of repositories to keep data in another location. The following types of repositories are supported for all repositories (the cache, primary and secondary repositories):

* Direct attached storage: [Microsoft Windows](ms_server.md) or [Linux](linux_server.md) virtual or physical machines. For the cache repository only 64-bit versions are supported.

* Network attached storage: [SMB (CIFS) shares](smb_share.md) or [NFS shares](nfs_share.md).

The following types of repositories are supported only for the primary and secondary log backup repositories:

* Direct attached storage: [Hardened repositories](hardened_repository.md)
* [Deduplicating storage appliances](deduplicating_storage_appliances.md): ExaGrid, Quantum DXi, Dell Data Domain or other

* [Backup repositories with rotated drives](backup_repository_rotated.md)

* [Object storage repositories](object_storage_repository.md): Amazon S3, S3 compatible, Google Cloud or other
* [Scale-out backup repositories (SOBR)](backup_repository_sobr.md)

|  |
| --- |
| Note |
| Veeam Backup for Microsoft Entra ID does not support using Veeam Cloud Connect repositories or multi-bucket repositories to store log backups. For more information, see section [Object Storage Repositories](object_storage_repository.md) and Veeam Cloud Connect Guide, section [Cloud Repository](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_repository.html?ver=13). |


