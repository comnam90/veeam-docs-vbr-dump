---
title: "Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_restore_how_entire.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Entire VM Restore


To restore a VM, Veeam Backup & Replication performs the following steps:

1. [This step applies only if you perform restore to the original location and if the source VM is still present in the location] Connects to the Proxmox VE server over REST API to power off and remove the source VM.
2. Launches a worker on same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other Proxmox VE host connected to the backup infrastructure.

1. Connects to the Proxmox VE server over REST API, configures a VM and creates empty virtual disks in the target location.

The number of empty disks equals the number of disks attached to the backed-up VM.

1. Restores backed-up data to the empty disks and restores them to the configured VM.

If multiple disks are attached to the backed-up VM, these disks are restored sequentially, one disk at a time.

1. Suspends the worker when the restore session completes.

|  |
| --- |
| Note |
| If multiple VMs are added to the restore session, these VMs are processed in parallel. |

To learn how to restore an entire VM, see [Performing VM Restore](pve_restore_entire_vm.md).


