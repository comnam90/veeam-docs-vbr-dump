---
title: "Disk Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_how_disk_restore.html"
last_updated: "8/12/2025"
product_version: "13.0.1.1071"
---

# Disk Restore


To restore a VM disk, Veeam Backup & Replication performs the following steps:

1. Connects to the Nutanix AHV server over REST API to power off the target VM.
2. Launches a worker on same host where the target VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches any other Nutanix AHV worker that is added to the backup infrastructure.

1. Creates empty virtual disks in the Nutanix AHV infrastructure.
2. Connects to the backup repository and restores backed-up data to the empty disks.
3. [Applies only if you restore the disks to the original VM and if you choose to replace the existing disks] Detaches the original disks from the VM and removes them from the Nutanix AHV infrastructure.
4. Attaches the created disks with the restored data to the target VM.

To learn how to restore a VM disk, see [Performing Disk Restore](ahv_restore_disks.md).


