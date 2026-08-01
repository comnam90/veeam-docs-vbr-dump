---
title: "Backup to Object Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_object_storage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup to Object Storage


If you want to store InterSystems IRIS backups in cloud-based or on-premises object storage, you can select an object storage repository as the target when creating an application backup policy. Veeam Backup & Replication supports object storage as a primary backup repository for application backup policies and as a capacity tier in a scale-out backup repository.

You can store InterSystems IRIS backups on the following types of object storage:

* Veeam Data Cloud Vault
* Amazon S3
* S3 compatible
* Google Cloud Storage
* Microsoft Azure Blob Storage
* IBM Cloud Object Storage
* Wasabi Cloud Storage
* 11:11 Cloud Object Storage

When you back up InterSystems IRIS instances to an object storage repository, backup data is transferred from the Linux-based backup proxy to the object storage according to the connection mode configured in the repository settings — via a gateway server or directly. For details about gateway servers, see [Gateway Servers](gateway_server.md).

|  |
| --- |
| Important |
| If you plan to use S3 compatible object storage, you must perform an extra step after adding the repository: manually configure access to the object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md). |

Getting Started

To back up InterSystems IRIS instance data to object storage, complete the following steps:

1. Review the object storage limitations listed in [Veeam Backup Repositories](iris_backup_repos.md#object).
2. Add the object storage as a backup repository in the Veeam Backup & Replication console. For details, see [Adding Object Storage Repositories](new_object_storage.md).

You can use object storage in Veeam Backup & Replication as either of the following repository types:

* Primary backup repository. For details, see [Backup Repositories](backup_repository.md).
* Capacity tier in a scale-out backup repository. For details, see [Scale-Out Backup Repositories](backup_repository_sobr.md).

1. [For S3 compatible object storage] Configure access to the object storage. For details, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).
2. Create an application backup policy and select the object storage repository from the list of available repositories. For details, see [Creating Application Backup Policy](iris_policy_create.md).

Page updated 2026-07-24

