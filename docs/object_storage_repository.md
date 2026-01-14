---
title: "Object Storage Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_repository.html"
last_updated: "12/11/2025"
product_version: "13.0.1.1071"
---

# Object Storage Repositories

In this article

An object storage repository is a repository intended for long-term data storage and based on either a cloud solution or S3 compatible on-premises storage solutions.

Veeam Backup & Replication supports the following types of object storage repositories:

* Veeam Data Cloud Vault
* Amazon S3, Amazon S3 Glacier and AWS Snowball Edge
* S3 compatible, S3 compatible with data archiving
* Google Cloud
* IBM Cloud
* Wasabi Cloud Storage
* Microsoft Azure Blob, Azure Archive Storage and Azure Data Box
* 11:11 Cloud Object Storage

You can use object storage repositories as target repositories in the following ways:

* As target repositories for [backup jobs](backup_job.md) and [backup copy jobs](backup_copy.md).

|  |
| --- |
| Tip |
| You can also use object storage repositories as a source location from which backup copy jobs will copy restore points. |

* As target repositories for [file backup jobs](unstructured_data_backup.md).

|  |
| --- |
| Important |
| You cannot keep backups created by file backup jobs in object storage repositories if they are added as performance extents of the scale-out backup repository. |

* As target repositories for backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication.

* As target repositories for backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md).
* As target repositories for backups of macOS physical machines created by [Veeam Agent for Mac](agents_backup_mac.md).

* As target repositories for backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9).
* As target repositories for backups of [Veeam Agent Backup](protect_comp.md).

* As target repositories for backups of oVirt created by [Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7).
* As target repositories for backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2).

* As target repositories for backups of applications running on Kubernetes persistent volumes created by Veeam Kasten Plug-In for Veeam Backup & Replication.

|  |
| --- |
| Note |
| You can keep backups of Kasten application in object storage repositories only in case they are used as the capacity or archive extents of a scale-out backup repository. You cannot back up Kasten application directly to backup object storage repositories or in case they are used as performance extents of a scale-out backup repository. |

* As target repositories for backups of [configuration database](export_vbr_config.md) created by Veeam Backup & Replication.
* As target repositories for backups of databases created by [Veeam Plug-Ins for Enterprise Applications](protect_applications.md#database-level).
* As target repositories for backups of MongoDB replica sets created by [MongoDB Backup](mongo_backup.md).

You can also use object storage repositories as the following parts of the scale-out backup repository:

* As a part of [Performance Tier](backup_repository_sobr_extents.md). Performance tier allows quickly accessing the stored data. For more information, see [Performance Tier](backup_repository_sobr_extents.md).
* As a part of [Capacity Tier](capacity_tier.md). Capacity tier of scale-out backup repository allows offloading the existing backup data directly to cloud-based object storage. For more information, see [Capacity Tier](capacity_tier.md).
* As a part of [Archive Tier](archive_tier.md). Archive tier of scale-out backup repository allows transporting the infrequently accessed data from the capacity tier for archive storage. For more information, see [Archive Tier](archive_tier.md).

Object Storage Repository Deployment

To communicate with an object storage repository, Veeam Backup & Replication uses the following components:

* [For VMware vSphere] A [VMware backup proxy](backup_proxy.md) — used to transfer data.
* [For Microsoft Hyper-V] Either an [on-host](onhost_backup.md) or [off-host backup proxy](offhost_backup_proxy.md) — used to transfer data.
* A [mount server](move_backup.md) — used to process guest OS applications and perform item recovery

Depending on the type of job, a backup proxy connects to the object storage repository using one of the following connection modes:

* Direct — in this mode, a backup proxy transfers data directly to the object storage repository. This connection type is used, for example, for backup and restore sessions when your target object storage repository is located in your local infrastructure.
* Through gateway servers — in this mode, a backup proxy transfers data to the object storage repository through a gateway server.

By default, Veeam Backup & Replication deploys object storage repositories with the direct connection mode. You can specify the connection mode at the Account step of the Object Storage Repository wizard.

Multiple Buckets for S3 Compatible Object Storage Repositories

To improve performance and provide scalability options, you can deploy S3 compatible object storage in multiple bucket mode. If you enable this option, Veeam Backup & Replication will provision child buckets automatically and will distribute backups between these buckets. The number of child buckets depends on the number of per-machine backup chains you want to keep in a single child bucket. Veeam Backup & Replication keeps in a single child bucket only a number of per-machine backup chains that you specify in the repository settings. If the capacity of the existing child buckets is full, Veeam Backup & Replication automatically creates new buckets. To maintain a connection between the backups and child buckets, Veeam Backup & Replication keeps the mapping metadata in the master bucket using the specified prefix.

For every child bucket Veeam Backup & Replication uses the MD5 algorithm to generate a standard name according to the following pattern: client ID + repository ID + timestamp (for example, dcb740b2c2836cb11f707d63e6ac664f). In case the creation of a new bucket fails (for example, due to lack of the necessary permissions), Veeam Backup & Replication writes backups to an existing child bucket that is less occupied. At the same time, Veeam Backup & Replication will try to create new child buckets on the next run of a job.

You can enable the option for new S3 compatible object storage repositories or existing repositories. To do this, you must enable the [necessary option in the S3 compatible repository wizard](compatible_storage_details.md#multiplebucket). You can use different S3 compatible object storage repositories to store backup mapping metadata in the same master bucket. In case you need to add to the backup infrastructure your S3 compatible object storage repositories with the multiple bucket option enabled, Veeam Backup & Replication will import backups from all child buckets and from the master bucket (in case there are any legacy backups there).

For limitations, see [Considerations and Limitations for S3 Compatible Repositories with Multiple Buckets](s3_compatible_limitations.md#multibucket).

For necessary permissions, see [Permissions for S3 Compatible Object Storage Repositories](required_permissions.md#rpasos).

In This Section

* [Considerations and Limitations](object_storage_repository_cal.md)
* [Health Check for Object Storage Repositories](health_check_os.md)
* [Object Storage Repository Structure](object_storage_structure.md)
* [Background Checkpoint Removal Job](checkpoint_removal_job.md)
* [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md)
* [Adding Object Storage Repositories](new_object_storage.md)
* [Managing Object Storage Repositories](managing_object_storage_repo_data.md)
* [Managing Object Storage Backups](managing_object_storage_backups.md)

Page updated 12/11/2025

Page content applies to build 13.0.1.1071
