---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_changed_block_tracking.html"
last_updated: "2/3/2026"
product_version: "13.0.1.1071"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Plug-in for Nutanix AHV to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Plug-in for Nutanix AHV reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Plug-in for Nutanix AHV reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on the Nutanix AHV REST API:

1. During the first (full) backup session, Veeam Plug-in for Nutanix AHV creates a snapshot of a VM using native Nutanix AHV capabilities. To do that, Veeam Plug-in for Nutanix AHV sends API requests to access the content of the snapshot and to detect unallocated data blocks.
2. During subsequent sessions, new snapshots are created. Veeam Plug-in for Nutanix AHV sends API requests to access and to compare the content of the snapshot created during the previous backup session and the snapshot created during the current backup session. This allows Veeam Plug-in for Nutanix AHV to detect data blocks that have changed since the previous backup session.

Limitations for Changed Block Tracking

Veeam Plug-in for Nutanix AHV does not use CBT for backup jobs which include a protection domain with consistency groups that contain two or more entities. If CBT cannot be used, Veeam Plug-in for Nutanix AHV reads the whole content of processed disks and compares it with backed-up data that already exists in the backup repository. In this case, the completion time of incremental backups may occur to grow.


