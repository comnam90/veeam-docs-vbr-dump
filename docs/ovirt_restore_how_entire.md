---
title: "Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_restore_how_entire.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Entire VM Restore


To restore a VM, Veeam Plug-in for oVirt KVM performs the following steps:

1. [Applies only if you restore the VM to the original location] Powers off and removes the original VM.
2. Launches a worker in the same cluster where the restored VM will reside.

If no worker is deployed in the cluster, Veeam Backup & Replication launches a worker that is deployed in any other cluster connected to the oVirt KVM Manager.

1. Connects to the oVirt KVM Manager over REST API, configures a VM and creates empty virtual disks in the target location.

The number of empty disks equals the number of disks attached to the backed-up VM.

1. Uses the worker to connect to the repository where backed-up data is stored, retrieves the data and restores it to the empty disks — and then attaches these disks to the configured VM. If multiple disks are attached to the backed-up VM, these disks are restored sequentially, one disk at a time.

If the backed-up VM originally resided on a platform other than oVirt KVM, Veeam Backup & Replication attaches disks with the restored data to the target oVirt KVM VM [in a specific order](ovirt_bus_type_restore_order.md).

1. Suspends the worker when the restore session completes.

|  |
| --- |
| Note |
| If multiple VMs are added to the restore session, these VMs are processed in parallel. |

To learn how to restore an entire VM, see [Performing VM Restore](ovirt_restore_to_rhv.md).


