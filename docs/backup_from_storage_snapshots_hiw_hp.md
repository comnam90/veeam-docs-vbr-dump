---
title: "Backup from Primary Storage Arrays"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_from_storage_snapshots_hiw_hp.html"
last_updated: "2/14/2025"
product_version: "13.0.1.1071"
---

# Backup from Primary Storage Arrays


Backup from primary storage array allows you to use the backup from storage snapshots feature and create backups from snapshots created on primary storage arrays.

How Backup from Primary Storage Works

When you run a job with backup from storage snapshots enabled, Veeam Backup & Replication performs the following actions:

1. Analyzes which VMs in the job host their disks on the storage system. Checks the backup infrastructure and detects if there is a backup proxy that has a direct connection to the storage system.
2. Triggers the vCenter Server to create VMware snapshots for these VMs.
3. Requests the ESXi host to retrieve metadata about the layout of VM disks (physical addresses of data blocks). Veeam Backup & Replication also gets Changed Block Tracking (CBT) information for VMs hosted on the storage system.
4. Instructs the storage system to create a temporary snapshot of the storage volume or LUN that hosts VM disks and VMware snapshots.
5. Instructs the vCenter Server to remove VMware VM snapshots. The "cloned" VMware snapshots remain on the created temporary storage snapshots.
6. Mounts the temporary storage snapshot as a new volume to this backup proxy.
7. Reads and transports VM data blocks through the backup proxy to the backup repository. For incremental backup or replication, Veeam Backup & Replication uses obtained CBT data to retrieve only changed data blocks from the temporary storage snapshot.
8. When VM data processing is finished, Veeam Backup & Replication unmounts the temporary storage snapshot from the backup proxy and instructs the storage system to remove the temporary storage snapshot.

![Backup from Primary Storage Arrays](images/storage_backup_hiw.webp)

Mixed Job Scenarios

Backup from storage snapshots is used only for those VMs whose disks are hosted on supported storage systems. As backup and replication jobs typically process a number of VMs that may reside on different types of storage, Veeam Backup & Replication processes VMs in mixed jobs in the following way:

* If a job processes a number of VMs whose disks are hosted on different types of storage, Veeam Backup & Replication uses backup from storage snapshots only for VMs whose disks are hosted on supported storage systems. Other VMs are processed in a regular manner.
* If a VM has several disks, some hosted on supported storage systems and some hosted on another type of storage, Veeam Backup & Replication does not use backup from storage snapshots to such VM. All disks of such VM are processed in a regular manner.

During a job, Veeam Backup & Replication processes VMs residing on different types of storage at different time:

1. Veeam Backup & Replication first triggers VMware snapshots and storage snapshots for VMs hosted on supported storage systems.
2. After the storage snapshot is created, Veeam Backup & Replication triggers VMware snapshots for other VMs. These VMs are processed in the regular data processing mode further on, in parallel with VMs whose disks are hosted on supported storage systems.

Related Topics

[Configuring Backup from Storage Snapshots](storage_backup.md)


