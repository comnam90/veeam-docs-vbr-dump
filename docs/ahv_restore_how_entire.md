---
title: "Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_how_entire.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Entire VM Restore


To restore a VM, Veeam Backup & Replication performs the following steps:

1. [Applies only if you perform restore to the original location where the source VM is still present] Connects to the Nutanix AHV server over REST API to power off and remove the source VM.
2. Launches a worker on same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches any other Nutanix AHV worker that is added to the backup infrastructure.

1. Connects to the target Nutanix AHV server over REST API and creates a VM in the target location.
2. Creates empty virtual disks in the target location. The number of empty disks equals the number of disks attached to the source VM.
3. Connects to the backup repository and restores backed-up data to the empty disks.

If multiple disks are attached to the source VM, Veeam Backup & Replication restores these disks sequentially, one disk at a time.

1. Attaches the created disks with the restored data to the target VM disk nodes using their original bus.

The maximum number of disk nodes available on Nutanix AHV VMs for each bus type is limited. Veeam Backup & Replication can attach to a VM up to 6 SATA, 256 SCSI, 4 IDE and 7 PCI disks. If you restore a VM that has more disks of any of those bus types, Nutanix AHV will attach the disks to remaining nodes of other bus types in the default priority: SATA, SCSI, IDE, PCI. You can modify [the Veeam Plug-in for Nutanix AHV configuration](ahv_bus_type_restore_order.md), to instruct Nutanix AHV to ignore original bus types and to use a specific order of bus types.

1. [Applies only if the VM has volume groups attached] Creates a new volume group with empty disks.
2. [Applies only if the VM has volume groups attached] Connects to the backup repository and restores backed-up data to the empty disks of the volume group.
3. [Applies only if the VM has volume groups attached and you perform restore to the original location where the source VM is still present] Removes the volume group that was attached to the source VM.
4. [Applies only if the VM has volume groups attached] Attaches the created volume group with the restored data to the target VM.

|  |
| --- |
| Note |
| Veeam Backup & Replication prioritizes restore tasks higher than other tasks. If multiple VMs are added to the restore session, these VMs are processed in parallel. |

To learn how to restore an entire VM, see [Performing VM Restore](ahv_restore_to_ahv.md).


