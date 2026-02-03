---
title: "Performing VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_to_ahv.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Performing VM Restore


In case a disaster strikes, you can restore an entire Nutanix AHV VM from a backup or snapshot. Veeam Plug-in for Nutanix AHV allows you to restore one or more VMs at a time, to the original location or to a new location.

Supported Workloads

To restore machines to a Nutanix AHV cluster, you can use the following backups and snapshots:

* Snapshots of Nutanix AHV PDs created manually in Nutanix AHVPrism Central or Prism Element console
* Snapshots of Nutanix AHV VMs created manually in Nutanix AHVPrism Central or Prism Element console
* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV (including VMs with volume groups attached and VMs with no disks attached)

* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication

* Backups of oVirt KVM VMs created by Veeam Plug-in for Oracle Linux Virtualization Manager and Red Hat Virtualization
* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE

* Backups of Scale Computing HyperCore VMs created by Veeam Plug-in for Scale Computing HyperCore

* Backups of VMs created by vCloud Director
* Backups of Amazon EC2 instances created by Veeam Backup for AWS

* Backups of Microsoft Azure VMs created by Veeam Backup for Microsoft Azure
* Backups of Google Cloud VM instances created by Veeam Backup for Google Cloud

* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux

VM restore is supported only for snapshots stored in the Nutanix AHV cluster and for backups stored in backup repositories, object storage repositories, and on the performance, capacity and archive tier of a scale-out backup repository (except for backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent; for those backups, you can perform [Instant Recovery](ahv_instant_recovery_ahv.md)).

|  |
| --- |
| Note |
| You cannot restore VMs from backups stored in external repositories, Veeam Cloud Connect repositories, HPE Cloud Bank Storage and on tapes. |

How to Perform VM Restore

From the Veeam Backup & Replication console, you can restore one or multiple VMs to any Nutanix AHV cluster added to the backup infrastructure.

To restore a protected VM, do the following:

1. [Check prerequisites and limitations](ahv_restore_to_ahv_byb.md).
2. [Launch the Full VM Restore wizard](ahv_restore_to_ahv_launch.md).
3. [Select VMs to restore](ahv_restore_to_ahv_select_vms.md).
4. [Choose a restore mode](ahv_restore_to_ahv_mode.md).
5. [Specify a target cluster](ahv_restore_to_ahv_target_cluster.md).
6. [Select a storage container where VM virtual disks will be stored](ahv_restore_to_ahv_container.md).
7. [Specify a new name for the restored VM](ahv_restore_to_ahv_vm_name.md).
8. [Configure network settings](ahv_restore_to_ahv_network.md).
9. [Specify a restore reason](ahv_restore_to_ahv_reason.md).
10. [Verify restore settings](ahv_restore_to_ahv_summary.md).


