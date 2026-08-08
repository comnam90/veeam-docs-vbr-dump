---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_changed_block_tracking.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Backup & Replication to reduce the amount of data read from processed VMs and to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Backup & Replication reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Backup & Replication reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on the checkpoint ID functionality:

1. During the first (full) backup session, Veeam Plug-in for Sangfor aSV takes a snapshot of a VM using native Sangfor aSV capabilities. Veeam Plug-in for Sangfor aSV sends API requests to detect unallocated data blocks and to access all written data blocks. The written data blocks are then stored in a backup repository as a single full backup file in the native Veeam format.

While processing the requests, Sangfor aSV creates a checkpoint ID for the backup session and saves the ID to the backup metadata. Checkpoint IDs allow Sangfor aSV to track data blocks that change between sessions.

1. During every subsequent session, a new snapshot is taken and a new checkpoint ID is created. Veeam Plug-in for Sangfor aSV sends API requests to Sangfor aSV to use the previous checkpoint ID to detect data blocks that have changed since the previous backup session. These data blocks are then stored in the backup repository as a single incremental backup file in the native Veeam format.

Page updated 2026-07-16

