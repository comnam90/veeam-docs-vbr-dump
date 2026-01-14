---
title: "Quick Migration for VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/quick_migration.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Quick Migration for VMware vSphere

In this article

Quick Migration allows you to migrate VMs or virtual disks between ESXi hosts and datastores. Veeam Backup & Replication supports migration of VMs or their disks in any state with minimum disruption to business operations. You can use Quick Migration as a self-contained capability or as a way to finalize the Instant Recovery and Instant Disk Recovery processes.

When you perform Quick Migration, Veeam Backup & Replication analyzes your virtual environment, its configuration, the state of VMs and selects the most appropriate VM relocation method:

* vMotion and Storage vMotion

vMotion and Storage vMotion are native migration mechanisms of VMware vCenter. Veeam Backup & Replication uses these methods whenever it is possible.

* Veeam Quick Migration

Veeam Quick Migration is the Veeam Backup & Replication proprietary technology. Veeam Backup & Replication uses this method when VMware vCenter methods cannot be used. For example, if your VMware vSphere license does not provide support for vMotion and Storage vMotion, or you need to migrate VMs from one standalone ESXi host to another.

Veeam Quick Migration supports two modes of VM migration:

* SmartSwitch

With SmartSwitch, Veeam Backup & Replication suspends a VM, then moves the VM configuration file and copies changes made to the VM disk after snapshot creation to the target host. After the migration is completed, the VM is resumed on the target host.

* ColdMigration

With ColdMigration, Veeam Backup & Replication stops the VM, then copies changes made to the VM disk after snapshot creation to the new host. After, the VM is started on the target host.

Veeam Quick Migration of VMs

Migration of a VM using the Veeam Quick Migration method includes the following steps:

1. Veeam Backup & Replication copies VM configuration file (.VMX) to the target host and registers the VM.
2. Veeam Backup & Replication triggers a VM snapshot creation and copies VM disk content to the new destination.
3. Veeam Backup & Replication uses different modes when moving the VM between hosts with compatible and non-compatible CPUs.

+ If you move a VM between two hosts with compatible CPUs, Veeam Backup & Replication uses the SmartSwitch mode.

+ If you move a VM between two hosts with non-compatible CPUs or VM RAM is more than 8 GB, Veeam Backup & Replication uses the ColdMigration mode.

Veeam Quick Migration of Virtual Disks

Migration of a VM disk using the Veeam Quick Migration method includes the following steps:

1. A temporary VM is created on the target datastore.
2. Veeam Backup & Replication copies the disk from the original datastore to the temporary VM on the target datastore.
3. If the original VM is powered on, Veeam Backup & Replication suspends it.
4. If changes were made to the original disk during the copy process performed at step 3, Veeam Backup & Replication copies these changes to the disk of the temporary VM.
5. On the original VM, Veeam Backup & Replication replaces old path to the disk with the path to the disk of the temporary VM.
6. If the original VM was suspended during the migration, Veeam Backup & Replication powers the VM on.

|  |
| --- |
| Important |
| Before the migration, VM disks must be recovered using [Instant Disk Recovery](instant_disk_recovery.md). |

Veeam Quick Migration of First Class Disks (FCDs)

Migration of First Class Disks (FCDs) supports only the vMotion method and includes the following steps:

1. Veeam Backup & Replication gets information about the target datastore.
2. Veeam Backup & Replication connects to one of the ESXi hosts of a cluster to which the target datastore is mounted.
3. Veeam Backup & Replication migrates FCDs from the source datastore to the target datastore.
4. If redo logs are stored on a custom datastore, Veeam Backup & Replication will delete FCDs snapshots after migration.
5. Veeam Backup & Replication assigns storage policies to FCDs.

Related Topics

* [Quick Migration Architecture](migration_architecture.md)
* [Migrating VMs](migration_job.md)
* [Instant Recovery to VMware vSphere](instant_recovery.md)

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
