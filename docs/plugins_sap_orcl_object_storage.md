---
title: "Backup to Object Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_orcl_object_storage.html"
last_updated: "8/6/2025"
product_version: "13.0.1.1071"
---

# Backup to Object Storage

In this article

If you want to store your data in a cloud-based or on-premises object storage, you can use Veeam Plug-In to create backups in repositories provided by the object storage. Veeam Plug-Ins support the object storage as a primary repository for backup jobs and Veeam Backup & Replication supports the object storage as a primary repository for backup copy jobs.

You can store backups created with Veeam Plug-Ins on the following types of the object storage:

* Amazon S3
* S3 compatible
* Google Cloud Storage
* Microsoft Azure Blob Storage
* IBM Cloud Object Storage
* Wasabi Cloud Storage
* Veeam Data Cloud Vault
* 11:11 Cloud Object Storage

Veeam Plug-In on the machine with the database always accesses object storage through Veeam Backup & Replication. As a result, Veeam Plug-In access to object storage is managed by a proxy component that Veeam Backup & Replication selects according to the connection mode specified in the repository settings:

* Connection through a gateway server. With this connection mode, Veeam Plug-Ins access object storage through a gateway server specified in the repository settings. Backup data is sent from computer with Veeam Plug-In to the gateway server, then it is sent from gateway server to the object storage. For details about gateway server, see [Gateway Servers](gateway_server.md).
* Direct connection. With this connection mode, Veeam Plug-Ins access object storage through a mount server specified in the repository settings. Backup data is sent from computer with Veeam Plug-In to the mount server, then it is sent from mount server to the object storage. The usage of the mount server allows Veeam Plug-In to avoid high CPU consumption on the machine with the database. For details about mount server, see [Mount Servers](mount_server.md).

|  |
| --- |
| IMPORTANT |
| * After you switch your repository from one connection mode to another, Veeam Plug-In will need to connect to Veeam Backup & Replication to update repository settings. Until this connection is made, all backup operations by Veeam Plug-In will fail.  * If you plan to back up data to the S3 compatible storage, you must perform an extra step: manually set access to the object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md). |

Getting Started

To back up database to an object storage, you must complete the following steps:

1. Add repository in the Veeam backup console. For details, see [Adding Object Storage Repositories](new_object_storage.md).

You can use an object storage in Veeam Backup & Replication as one of the following repositories:

* Backup repository. For details, see [Backup Repositories](backup_repository.md).
* Scale-out backup repository added as a Veeam backup repository. For details, see [Scale-Out Backup Repositories](backup_repository_sobr.md).

1. [For S3 compatible object storage] Set access to the added S3 compatible object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).
2. Create an application backup policy and select the object storage from the list of available repositories.

To learn more, see [Creating Application Backup Policy](mongo_policy_create.md).

|  |
| --- |
| Note |
| Before you configure your backup infrastructure to back up to the object storage, consider the limitations listed in [Veeam Backup Repositories](sap_orcl_repos.md#object). |

Page updated 8/6/2025

Page content applies to build 13.0.1.1071
