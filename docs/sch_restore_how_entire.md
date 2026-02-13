---
title: "Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_restore_how_entire.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Entire VM Restore


To restore a VM, Veeam Plug-in for Scale Computing HyperCore performs the following steps:

1. [This step applies only if you perform restore to the original location and if the source VM is still present in the location] Powers off and removes the source VM.
2. Launches a worker on same host where the processed VM resides.

If no worker is deployed on the host, Veeam Plug-in for Scale Computing HyperCore launches a worker that is deployed on any other Scale Computing HyperCore host connected to the backup infrastructure.

1. Creates a new VM with source VM settings without disks.
2. Restores each VM disk sequentially:

1. Creates a disk on a worker and restores data from a backup to it.
2. Creates a snapshot of the worker VM.
3. Creates a clone of a worker VM snaphot disk on a new VM.
4. Removes the worker VM snapshot.

1. Powers on a restored VM, if automatic power on is enabled.
2. Suspends the worker when the restore session completes.

|  |
| --- |
| Note |
| If you initiate restore of multiple VMs, a separate restore session is started for each VM. |

To learn how to restore an entire VM, see [Performing VM Restore](sch_restore_entire_vm.md).


