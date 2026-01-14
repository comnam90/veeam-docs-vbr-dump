---
title: "VMware Integration (Storage Systems)"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vmware_integration.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# VMware Integration (Storage Systems)

In this article

To build the data protection and disaster recovery strategy, you can use the capabilities of native snapshots created on production storage systems that host VM disks.

Veeam Backup & Replication provides the following options to use native snapshots:

* [Backup from storage snapshots](backup_from_storage_snapshots.md). You can use storage snapshots to create backups and replicas of VMware vSphere VMs hosted on storage systems. Backup from Storage Snapshots speeds up backup and replication operations and reduces the impact of VMware snapshot removal on the production environment.
* [Snapshot orchestration](schedule_snapshots.md). You can configure jobs to periodically create storage snapshots on primary or secondary storage arrays.
* [Backup from storage snapshots with snapshot retention](snapshot_job_secondary_perform.md). You can configure backup jobs to create backup files in the backup repository and, additionally, storage snapshots on the primary or secondary storage arrays.
* [Data recovery from storage snapshots](storage_snapshots_restore.md). You can restore VM data directly from storage snapshots. Restore from Storage Snapshots automates the process of VM data recovery and reduces recovery time in 10 times or more.
* [On-Demand sandbox for storage snapshots](sandbox_storages_ebook.md). You can start VMs whose disks are hosted on storage systems in the On-Demand Sandbox. On-Demand Sandbox can be used for testing, training, troubleshooting and so on.
* [Creation and deletion of snapshots manually](storage_create_snapshot.md). You can create and delete storage snapshots in the Veeam Backup & Replication console.

|  |
| --- |
| Important |
| Consider the following:   * To start working with storage systems, you must properly configure the backup infrastructure. For more information, see [Infrastructure Overview](storage_infrastructure.md). After that, you can use storage snapshots for data protection and disaster recovery operations. * Detailed information about which storage systems support Backup from Storage Snapshot and snapshot orchestration, and which native storage features Veeam Backup & Replication supports is provided in [Supported Features for Backup and Orchestration](supported_features.md). * Cisco HyperFlex HX-Series storage system does not support manual creation and deletion of storage snapshots, and data recovery from storage snapshots. |

In This Section

* [Supported Storage Features for Backup and Orchestration](supported_features.md)
* [Backup from Storage Snapshots](backup_from_storage_snapshots.md)
* [Backup from Cisco HyperFlex Snapshots](cisco_integration.md)
* [Snapshot Orchestration](schedule_snapshots.md)
* [Backup from Storage Snapshots with Snapshot Retention](snapshot_job_secondary.md)
* [Data Recovery from Storage Snapshots](storage_snapshots_restore.md)
* [Retrieving Achived Snapshots](storage_archived.md)
* [Creating and Deleting Snapshots](storage_create_snapshot.md)

Page updated 10/17/2025

Page content applies to build 13.0.1.1071
