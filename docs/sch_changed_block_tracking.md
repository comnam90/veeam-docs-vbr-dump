---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_changed_block_tracking.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Plug-in for Scale Computing HyperCore to reduce the amount of data read from processed VMs, and to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Plug-in for Scale Computing HyperCore reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Plug-in for Scale Computing HyperCore reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks:

1. During the first (full) backup session, Veeam Plug-in for Scale Computing HyperCore creates a snapshot of a VM using native Scale Computing HyperCore capabilities.
2. During subsequent sessions, new snapshots are created. Veeam Plug-in for Scale Computing HyperCore compares the content of the snapshot created during the previous backup session and the snapshot created during the current backup session. This allows Veeam Plug-in for Scale Computing HyperCore to detect data blocks that have changed since the previous backup session.


