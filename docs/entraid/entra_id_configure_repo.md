---
title: "Configuring Log and Cache Repositories"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_configure_repo.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Configuring Log and Cache Repositories


To protect Microsoft Entra ID tenant data and logs, you require the following repositories:

* Cache repository that stores temporary cache files for log processing.
* Primary log backup repository.
* [Optional] Secondary backup repository that stores copies of backups.

By default, the backup server can perform the roles of cache and primary log backup repositories.

You can also configure other types of repositories to keep data in another location. The following types of repositories are supported for all repositories (the cache, primary and secondary repositories):

* Direct attached storage: [Microsoft Windows](https://helpcenter.veeam.com/docs/vbr/userguide/ms_server.html?ver=13) or [Linux](https://helpcenter.veeam.com/docs/vbr/userguide/linux_server.html?ver=13) virtual or physical machines. For the cache repository only 64-bit versions are supported.

* Network attached storage: [SMB (CIFS) shares](https://helpcenter.veeam.com/docs/vbr/userguide/smb_share.html?ver=13) or [NFS shares](https://helpcenter.veeam.com/docs/vbr/userguide/nfs_share.html?ver=13).

The following types of repositories are supported only for the primary and secondary log backup repositories:

* Direct attached storage: [Hardened repositories](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository.html)
* [Deduplicating storage appliances](https://helpcenter.veeam.com/docs/vbr/userguide/deduplicating_storage_appliances.html?ver=13): ExaGrid, Quantum DXi, Dell Data Domain or other

* [Backup repositories with rotated drives](https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_rotated.html?ver=13)

* [Object storage repositories](https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_repository.html?ver=13): Amazon S3, S3 compatible, Google Cloud or other
* [Scale-out backup repositories (SOBR)](https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_sobr.html?ver=13)

|  |
| --- |
| Note |
| Veeam Backup for Microsoft Entra ID does not support using Veeam Cloud Connect repositories or multi-bucket repositories to store log backups. For more information, see the Veeam Cloud Connect Guide, section [Cloud Repository](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_repository.html?ver=13) and Veeam Backup & Replication User Guide, section [Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_repository.html?ver=13#childbuckets). |


