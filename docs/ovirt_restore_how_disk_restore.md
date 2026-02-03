---
title: "Disk Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_restore_how_disk_restore.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# Disk Restore


To restore a VM disk, Veeam Plug-in for oVirt KVM performs the following steps:

1. Powers off the target VM.
2. [Applies only if you restore disks to the original VM and if you choose to replace existing disks] Detaches the original disks from the VM and removes them from the oVirt KVM environment.
3. Launches a worker on the host where the target VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other oVirt KVM host.

1. Creates empty virtual disks in the target storage domain.

The number of empty disks equals the number of disks you selected to restore.

1. Restores backed-up data to the empty disks.
2. Attaches disks with restored data to the target VM.
3. Suspends the worker when the restore session completes.

To learn how to restore a VM disk, see [Performing Disk Restore](ovirt_restore_disks.md).


