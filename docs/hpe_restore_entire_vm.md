---
title: "Performing VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_restore_entire_vm.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Performing VM Restore


In case of a disaster, you can restore an entire HPE Morpheus VM Essentials VM from a backup. Veeam Backup & Replication allows you to restore one or more VMs at a time, to the original location or to a new location.

To restore machines to HPE Morpheus VM Essentials, you can use the following backups:

* Backups of HPE Morpheus VM Essentials VMs created by Veeam Plug-in for HPE Morpheus VM Essentials

* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV
* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE

* Backups of oVirt VMs created by Veeam Plug-in for oVirt KVM

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
| You cannot restore VMs from backups stored in external repositories, Veeam Cloud Connect repositories, HPE Cloud Bank Storage and on tapes. However, you can copy backups to a supported repository and then use them to restore VMs. |

To restore a protected VM, do the following:

1. [Launch the Entire VM Restore wizard](hpe_restore_entire_vm_launch.md).
2. [Select a restore point](hpe_restore_entire_vm_select_vms.md).
3. [Choose a restore mode](hpe_restore_entire_vm_mode.md).
4. [Specify a target cluster](hpe_restore_entire_vm_target.md).
5. [Select a storage where VM virtual disks will be stored](hpe_restore_entire_vm_storage.md).
6. [Specify a name for the restored VM](hpe_restore_entire_vm_name.md).
7. [Configure network settings](hpe_restore_entire_vm_network.md).
8. [Specify a restore reason](hpe_restore_entire_vm_reason.md).
9. [Verify restore settings](hpe_restore_entire_vm_summary.md).


