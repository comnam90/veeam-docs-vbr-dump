---
title: "Backup to Object Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_object_storage.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Backup to Object Storage


If you want to store your data in a cloud-based or on-premises object storage, you can use MongoDB Backup to create backups in repositories provided by the object storage. Veeam Backup & Replication supports the object storage as a primary repository for application backup policies and backup copy jobs.

You can store backups created with MongoDB Backup on the following types of the object storage:

* Veeam Data Cloud Vault
* Amazon S3
* S3 compatible
* Google Cloud Storage
* Microsoft Azure Blob Storage
* IBM Cloud Object Storage
* Wasabi Cloud Storage
* 11:11 Cloud Object Storage

Veeam Agent on the machine with MongoDB replica set always accesses object storage through Veeam Backup & Replication. As a result, Veeam Agent access to object storage is managed by a proxy component that Veeam Backup & Replication selects according to the connection mode specified in the repository settings:

* Connection through a gateway server. With this connection mode, Veeam Agents access object storage through a gateway server specified in the repository settings. Backup data is sent from Veeam Agent computer to the gateway server, then it is sent from gateway server to the object storage. For details about gateway server, see [Gateway Servers](gateway_server.md).
* Direct connection. With this connection mode, Veeam Agents access object storage through a mount server specified in the repository settings. Backup data is sent from Veeam Agent computer to the mount server, then it is sent from mount server to the object storage. The usage of the mount server allows Veeam Agent to avoid high CPU consumption on the machines with the replica set. For details about mount server, see [Mount Servers](mount_server.md).

|  |
| --- |
| IMPORTANT |
| * After you switch your repository from one connection mode to another, Veeam Agent will need to connect to Veeam Backup & Replication to update repository settings. Until this connection is made, all backup operations by Veeam Agent will fail.  * If you plan to back up data to the S3 compatible storage, you must perform an extra step: manually set access to the object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md). |

Getting Started

To back up MongoDB replica set data to an object storage, you must complete the following steps:

1. Consider the limitations listed in [Veeam Backup Repositories](mongo_backup_repos.md#object).
2. Add repository in the Veeam backup console. For details, see [Adding Object Storage Repositories](new_object_storage.md).

You can use an object storage in Veeam Backup & Replication as one of the following repositories:

* Backup repository. For details, see [Backup Repositories](backup_repository.md).
* Scale-out backup repository added as a Veeam backup repository. For details, see [Scale-Out Backup Repositories](backup_repository_sobr.md).

1. [For S3 compatible object storage] Set access to the added S3 compatible object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).
2. Create an application backup policy and select the object storage from the list of available repositories.

To learn more, see [Creating Application Backup Policy](mongo_policy_create.md).


