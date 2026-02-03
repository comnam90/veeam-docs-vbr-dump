---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_changed_block_tracking.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Plug-in for oVirt KVM to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Plug-in for oVirt KVM reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Plug-in for oVirt KVM reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on the oVirt KVM [checkpoint ID functionality](https://www.ovirt.org/develop/incremental-backup-guide/incremental-backup-guide.html):

1. During the first (full) backup session, Veeam Plug-in for oVirt KVM takes a snapshot of a VM using native oVirt KVM capabilities. Veeam Plug-in for oVirt KVM sends API requests to detect unallocated data blocks and to access all written data blocks. The written data blocks are then stored in a backup repository as a single full backup file in the native Veeam format.

While processing the requests, oVirt KVM creates a checkpoint ID for the backup session and saves the ID to the backup metadata. Checkpoint IDs allow oVirt KVM to track data blocks that change between sessions.

1. During every subsequent session, a new snapshot is taken and a new checkpoint ID is created. Veeam Plug-in for oVirt KVM sends API requests to oVirt KVM to use the previous checkpoint ID to detect data blocks that have changed since the previous backup session. These data blocks are then stored in the backup repository as a single incremental backup file in the native Veeam format.

|  |
| --- |
| Note |
| VM snapshots taken during backup sessions are not kept in oVirt KVM forever — Veeam Plug-in for oVirt KVM deletes every snapshot once the session completes. |

Limitations for Changed Block Tracking

Due to oVirt KVM technical limitations, checkpoint IDs are not created for disks in the RAW format. Therefore, Veeam Plug-in for oVirt KVM will not be able to use CBT when processing VMs with RAW disks attached. If CBT cannot be used, Veeam Plug-in for oVirt KVM reads the whole content of VM disks and compares it with backed-up data that already exists in backup repositories. In this case, the completion time of incremental backups may occur to grow.

|  |
| --- |
| Note |
| This limitation does not apply to disks in the QCOW2 format. |

|  |
| --- |
| Important |
| If Veeam Plug-in for oVirt KVM is unable to use CBT while creating incremental backups, you may get the following warnings in backup session logs:   * "Unable to backup disks incrementally, using full scan backup".   To resolve this issue, check the oVirt KVM configuration as described in the [Veeam KB article](https://www.veeam.com/kb4208).   * "The Disk id=<disk id> has RAW format and can be backed up only in full scan mode".   To resolve this issue, convert the disk format to QCOW2 as described in the [Veeam KB article](https://www.veeam.com/kb4345). |


