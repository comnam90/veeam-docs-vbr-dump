---
title: "Performing VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_restore_entire_vm.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Performing VM Restore


In case of a disaster, you can restore an entire Proxmox VE VM from a backup. Veeam Backup & Replication allows you to restore one or more VMs at a time, to the original location or to a new location.

To restore machines to Proxmox VE, you can use the following backups:

* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE

* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV

* Backups of oVirt KVM VMs created by Veeam Plug-in for Oracle Linux Virtualization Manager and Red Hat Virtualization

* Backups of Scale Computing HyperCore VMs created by Veeam Plug-in for Scale Computing HyperCore

* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication

* Backups of VMs created by vCloud Director
* Backups of Amazon EC2 instances created by Veeam Backup for AWS

* Backups of Microsoft Azure VMs created by Veeam Backup for Microsoft Azure
* Backups of Google Cloud VM instances created by Veeam Backup for Google Cloud

* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux

VM restore is supported only for backups stored in backup repositories, object storage repositories and on the performance, capacity and archive tier of a scale-out backup repository (except for backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent).

|  |
| --- |
| Note |
| You cannot restore VMs from backups stored in external repositories, Veeam Cloud Connect repositories, and on tapes. |

To restore a protected VM, do the following:

1. [Launch the Entire VM Restore wizard](pve_restore_entire_vm_launch.md).
2. [Select a restore point](pve_restore_entire_vm_select_vms.md).
3. [Choose a restore mode](pve_restore_entire_vm_mode.md).
4. [Specify a target cluster](pve_restore_entire_vm_target.md).
5. [Select a storage where VM virtual disks will be stored](pve_restore_entire_vm_storage.md).
6. [Specify a name for the restored VM](pve_restore_entire_vm_name.md).
7. [Configure network settings](pve_restore_entire_vm_network.md).
8. [Specify a restore reason](pve_restore_entire_vm_reason.md).
9. [Verify restore settings](pve_restore_entire_vm_summary.md).


