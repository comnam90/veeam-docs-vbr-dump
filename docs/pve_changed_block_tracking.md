---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_changed_block_tracking.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Backup & Replication to reduce the amount of data read from processed VMs and to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Backup & Replication reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Backup & Replication reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on the QEMU Dirty Bitmaps functionality:

1. During the first (full) backup session, Veeam Backup & Replication [creates a bitmap](https://qemu-project.gitlab.io/qemu/interop/bitmaps.html) for each disk that is attached to a processed VM.
2. During subsequent sessions, Veeam Backup & Replication uses the created bitmaps to compare the contents of disks backed up during the previous backup session and the current disk contents. This allows Veeam Backup & Replicationto detect data blocks that have changed since the previous backup session. As soon as a new backup is created, Veeam Backup & Replication updates the bitmaps to include the latest changes.

Limitations for Changed Block Tracking

Due to Proxmox VE technical limitations, bitmaps created for disks in the RAW and VMDK formats are automatically removed as soon as VMs that have these disks attached are powered off or restarted. Therefore, Veeam Backup & Replication may not be able to use CBT when processing those VMs and trying to detect data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads the whole content of VM disks and compares it with backed-up data that already exists in backup repositories. In this case, the completion time of incremental backups may occur to grow.

|  |
| --- |
| Note |
| This limitation does not apply to disks in the QCOW2 format. |


