---
title: "Performing VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_restore_entire_vm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing VM Restore


In case of a disaster, you can restore an entire Sangfor aSV VM from a backup. Veeam Backup & Replication allows you to restore one or more VMs at a time, to the original location or to a new location.

To restore machines to Sangfor aSV, you can use the following backups:

* Backups of Sangfor aSV VMs created by Veeam Plug-in for Sangfor aSV

* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV

* Backups of oVirt KVM VMs created by Veeam Plug-in for oVirt KVM
* Backups of Proxmox VE VMs created by Veeam Plug-In for Proxmox VE

* Backups of Scale Computing HyperCore VMs created by Veeam Plug-in for Scale Computing HyperCore
* Backups of Xen VMs created by Veeam Plug-in for Xen
* Backups of HPE Morpheus VM Essentials VMs created by Veeam Plug-in for HPE Morpheus VM Essentials

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

1. [Launch the Entire VM Restore wizard](sangfor_restore_entire_vm_launch.md).
2. [Select a restore point](sangfor_restore_entire_vm_select_vms.md).
3. [Choose a restore mode](sangfor_restore_entire_vm_mode.md).
4. [Specify a target cluster](sangfor_restore_entire_vm_target.md).
5. [Select a target group](sangfor_restore_entire_vm_group.md).
6. [Select a storage where VM virtual disks will be stored](sangfor_restore_entire_vm_storage.md).
7. [Specify a name for the restored VM](sangfor_restore_entire_vm_name.md).
8. [Configure network settings](sangfor_restore_entire_vm_network.md).
9. [Specify a restore reason](sangfor_restore_entire_vm_reason.md).
10. [Verify restore settings](sangfor_restore_entire_vm_summary.md).

Page updated 2026-07-14

