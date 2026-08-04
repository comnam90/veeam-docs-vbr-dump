---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_changed_block_tracking.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows Veeam Plug-in for Xen to reduce the amount of data read from processed VMs, and to increase the speed and efficiency of incremental backups:

* During a full backup session Veeam Plug-in for Xen reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, Veeam Plug-in for Xen reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks:

1. During the first (full) backup session, Veeam Plug-in for Xen creates a snapshot of a VM using native Xen capabilities.
2. During subsequent sessions, new snapshots are created. Veeam Plug-in for Xen compares the content of the snapshot created during the previous backup session and the snapshot created during the current backup session. This allows Veeam Plug-in for Xen to detect data blocks that have changed since the previous backup session.

|  |
| --- |
| Note |
| CBT is not supported for GlusterFS and Xostor storage repositories. During each backup job run, Veeam Plug-in for Xen creates a full backup of disks that reside on such repositories. |

Page updated 2026-07-22

