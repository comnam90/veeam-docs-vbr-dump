---
title: "VM Restore from Tape to Infrastructure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_restore_from_tape.html"
last_updated: "6/21/2023"
product_version: "13.0.1.1071"
---

# VM Restore from Tape to Infrastructure


Restoring a VM from tape with Veeam Backup & Replication is a lot like restoring a VM from disk. For example, you can choose a desired restore point, select the target location or change the configuration of the restored VM.

To restore a VM from tape, you can choose between the following options:

* Restore VMs directly to infrastructure.
* Restore VMs through a staging repository.

To choose the needed option, select Restore directly to the infrastructure or Restore through the staging repository at the Backup Repository step of the Full VM Restore wizard. For more information, see [Choose Backup Repository](restore_vms_from_tape_staging.md).

You can restore only backups of VMware and Hyper-V virtual machines from tape to infrastructure. For backups of virtual machines running on other platforms and physical machine backups, use [Backup Restore from Tape to Repository](vm_restore_from_tape_to_repository.md) with further VM restore to infrastructure/VM file restore if necessary.

Restore Directly to Infrastructure

When you restore VMs from tape directly to the infrastructure, the restore process publishes the VMs to the virtual infrastructure copying the VM data directly from tape. This option is recommended if you want to restore one VM or a small number of VMs from a large backup that contains a lot of VMs. In this case, you do not need to provide a staging repository for a large amount of data most of which is not needed to you at the moment.

This option is not recommended in the following cases:

* If you want to restore a large number of VMs.
* If you used parallel processing to record the VM backup.

In these cases, the restore may be very slow because the required blocks of data may be located on tapes randomly. The restore process may require a lot of rewinding of tapes as tapes do not provide random access to data.

|  |
| --- |
| Note |
| If the list of proxies to use for direct restore contains a Linux proxy, only the Appliance mode (HotAdd) is available for the source VM disks that will be processed using this Linux proxy. The Appliance mode (HotAdd) has a number of requirements and limitations described in [this KB article](https://www.veeam.com/kb1054).  If disks cannot be processed in the Appliance mode (HotAdd), the VM restore fails. |

Restore Through Staging Repository

When you restore VMs from tape through a staging repository, the restore process temporarily copies the whole restore point to a backup repository or a folder on disk. After that Veeam starts a regular VM restore.

This option is recommended if you want to restore a lot of VMs from a backup as the disk provides a much faster access to random data blocks than tape.

Related Topics

* [How Restoring VM from Tape to Infrastructure Works](tape_restoring_vm_from_tape.md)
* [Restoring VM from Tape to Infrastructure](restoring_vms_from_tape.md)


