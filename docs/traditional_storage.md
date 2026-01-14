---
title: "Restore With and Without Veeam Backup & Replication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/traditional_storage.html"
last_updated: "1/19/2024"
product_version: "13.0.1.1071"
---

# Restore With and Without Veeam Backup & Replication

In this article

This section describes differences between restore from storage snapshots with and without Veeam Backup & Replication.

Manual Restore Without Veeam Backup & Replication

In virtual environments, restore from storage snapshots can be difficult. Storage snapshots are created per-volume, and one volume typically hosts disks of several VMs. For this reason, restore from storage snapshots is not a simple rollback operation — it is a multi-task process.

If restore from storage snapshots is performed manually, you must do the following:

1. On the storage system, perform operations to make the storage snapshot available on the ESXi host.
2. On the ESXi host, perform an HBA rescan.
3. Mount the storage snapshot to an ESXi host.
4. Browse the storage snapshot to locate VM files.
5. Add the VM to the inventory or copy VM files to another VMFS datastore.
6. Power on the VM.
7. Perform restore operations.
8. Perform cleanup operations after VM data restore is complete.

As a result, the restore process takes much time. If you need to restore guest OS files and application objects from a VM on the storage snapshot, the procedure will be even more complicated.

Restore With Veeam Backup & Replication

If you recover data from storage snapshots using Veeam Backup & Replication, storage snapshots are mounted to ESXi hosts automatically. You only need to select an ESXi host where the storage snapshot will be mounted, all other operations are performed automatically.

When you restore data from storage snapshots, they are not converted into backups. VM data is restored directly from native storage system snapshots. You do not have to install any agents or perform additional configuration actions.

Page updated 1/19/2024

Page content applies to build 13.0.1.1071
