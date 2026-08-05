---
title: "Disk Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_restore_how_disk_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disk Restore


To restore a VM disk, Veeam Backup & Replication performs the following steps:

1. Powers off the target VM.
2. [Applies only if you choose to replace existing disks] Detaches the original disks from the VM and removes them from the universal hypervisor environment.
3. Launches a worker on the host where the target VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other universal hypervisor host.

1. Creates empty virtual disks in the target storage domain.

The number of empty disks equals the number of disks you selected to restore.

1. Restores backed-up data to the empty disks.
2. Attaches disks with restored data to the target VM.
3. Suspends the worker when the restore session completes.

To learn how to restore a VM disk, see [Performing Disk Restore](uh_restore_disks.md).

Page updated 2026-07-10

