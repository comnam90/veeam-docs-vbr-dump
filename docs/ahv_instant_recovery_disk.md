---
title: "Instant Disk Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_instant_recovery_disk.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Instant Disk Recovery


With Instant Disk Recovery, you can immediately restore VM disks from a backup file and publish them in their initial format. Before you start an Instant Disk Recovery operation, check the following prerequisites:

* The target cluster runs Nutanix AOS 6.0 or later.
* The target cluster is [added to the backup infrastructure](ahv_add_ahv_cluster.md).

Supported Workloads

To recover VM disks to a Nutanix AHV cluster, you can use the following backups:

* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV

* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication

* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux
* Backups of VMs created by vCloud Director
* Backups of Amazon EC2 instances created by Veeam Plug-in for AWS

* Backups of Microsoft Azure VMs created by Veeam Plug-in for Microsoft Azure
* Backups of Google Cloud VMs instances created by Veeam Plug-in for Google Cloud

* Backups of oVirt VMs created by Veeam Plug-in for oVirt KVM
* Backups of HPE Morpheus VM Essentials VMs created by Veeam Plug-in for HPE Morpheus VM Essentials
* Backups of Scale Computing HyperCore VMs created by Scale Computing HyperCore

* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE

Instant Disk Recovery is not supported from:

* Backups of VMs with the ARM CPU architecture
* File-level backups created by Kasten 10, Veeam Agent for Linux, Veeam Agent for Microsoft Windows, Veeam Agent for Unix, Veeam Agent for Mac

How Instant Disk Recovery Works

When Instant Disk Recovery is performed, Veeam Plug-in for Nutanix AHV mounts a workload image to a mount server directly from a compressed and deduplicated backup file. Since there is no need to extract the workload from the backup file and copy it to production storage, you can perform recovery from any restore point in a matter of minutes.

The workload image remains in the read-only state to avoid unexpected modifications. By default, all changes to virtual disks that take place while the recovered workload is running are logged to auxiliary redo log files residing in the cluster. These changes are either merged if you choose to migrate the workload to the production environment, or discarded if you choose to revert the recovery operation.

How to Perform Instant Disk Recovery

To perform Instant Recovery of a protected disk, do the following:

1. [Check prerequisites and limitations](ahv_ir_disk_limitations.md).
2. [Launch the Instant Disk Recovery wizard](ahv_recovery_disks_launch.md).
3. [Select a VM](ahv_recovery_disks_select_disks.md).
4. [Select a restore point](ahv_recovery_disks_restore_point.md).
5. [Configure disk mapping](ahv_recovery_disks_mapping.md)
6. [Specify a restore reason](ahv_recovery_disks_reason.md).
7. [Finalize the instant recovery operation](ahv_recovery_disks_summary.md).

Related Topics

[Mount Server](mount_server.md)

Page updated 2026-07-17

