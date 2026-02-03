---
title: "Performing VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_restore_to_rhv.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Performing VM Restore


In case a disaster strikes, you can restore an entire oVirt VM from a backup. Veeam Plug-in for oVirt KVM allows you to restore one or more VMs at a time, to the original location or to a new location.

Supported Workloads

To restore machines to a oVirt KVM cluster, you can use the following backups:

* Backups of oVirt VMs created by Veeam Plug-in for oVirt KVM (including VMs with volume groups attached and VMs with no disks attached).
* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication.
* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux.
* Backups of VMs created by vCloud Director.
* Backups of Amazon EC2 instances created by Veeam Backup for AWS.
* Backups of Microsoft Azure VMs created by Veeam Backup for Microsoft Azure.
* Backups of Google Cloud VM instances created by Veeam Backup for Google Cloud.
* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV.
* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE.
* Backups of Scale Computing VMs created by Veeam Plug-in for Scale Computing HyperCore.

VM restore is supported only for backups stored in backup repositories, object storage repositories, and on the performance, capacity and archive tier of a scale-out backup repository (except for backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent).

|  |
| --- |
| Note |
| You cannot restore VMs from backups stored in external repositories and on tapes. However, you can copy backups to a supported repository and then use them to restore VMs. |

How to Perform VM Restore

To restore a protected VM, do the following:

1. [Launch the Full VM Restore to oVirt KVM wizard](ovirt_restore_to_rhv_launch.md).
2. [Select a restore point](ovirt_restore_to_rhv_select_vms.md).
3. [Choose a restore mode](ovirt_restore_to_rhv_mode.md).
4. [Specify a target cluster](ovirt_restore_to_rhv_target_cluster.md).
5. [Select a storage domain where VM virtual disks will be stored](ovirt_restore_to_rhv_container.md).
6. [Specify a name for the restored VM](ovirt_restore_to_rhv_vm_name.md).
7. [Configure network settings](ovirt_restore_to_rhv_network.md).
8. [Specify a restore reason](ovirt_restore_to_rhv_reason.md).
9. [Verify restore settings](ovirt_restore_to_rhv_summary.md).


