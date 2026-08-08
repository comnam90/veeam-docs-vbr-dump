---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_changed_block_tracking.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changed Block Tracking


[Applies only to hypervisors that support CBT]

The changed block tracking (CBT) mechanism allows Veeam Plug-in for Universal Hypervisor API to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Plug-in for Universal Hypervisor API reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Plug-in for Universal Hypervisor API reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on the oVirt KVM [checkpoint ID functionality](https://www.ovirt.org/develop/incremental-backup-guide/incremental-backup-guide.html):

1. During the first (full) backup session, Veeam Plug-in for Universal Hypervisor API takes a snapshot of a VM using native hypervisor capabilities. Veeam Plug-in for Universal Hypervisor API sends API requests to detect unallocated data blocks and to access all written data blocks. The written data blocks are then stored in a backup repository as a single full backup file in the native Veeam format.

While processing the requests, the hypervisor creates a checkpoint ID for the backup session and saves the ID to the backup metadata. Checkpoint IDs allow the hypervisor to track data blocks that change between sessions.

1. During every subsequent session, a new snapshot is taken and a new checkpoint ID is created. Veeam Plug-in for Universal Hypervisor API sends API requests to the hypervisor to use the previous checkpoint ID to detect data blocks that have changed since the previous backup session. These data blocks are then stored in the backup repository as a single incremental backup file in the native Veeam format.

|  |
| --- |
| Note |
| VM snapshots taken during backup sessions are not kept on the hypervisor forever — Veeam Plug-in for Universal Hypervisor API deletes every snapshot once the session completes. |

Limitations for Changed Block Tracking

Due to hypervisor technical limitations, checkpoint IDs are not created for disks in the RAW format. Therefore, Veeam Plug-in for Universal Hypervisor API will not be able to use CBT when processing RAW disks attached to VMs. If CBT cannot be used, Veeam Plug-in for Universal Hypervisor API reads the whole content of VM disks and compares it with backed-up data that already exists in backup repositories. In this case, it may take Veeam Backup & Replication more time to create incremental backups.

|  |
| --- |
| Note |
| This limitation does not apply to disks in the QCOW2 format. |

Page updated 2026-07-24

