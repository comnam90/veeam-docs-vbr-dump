---
title: "Snapshot Hunter"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/snapshot_hunter.html"
last_updated: "2/10/2025"
product_version: "13.0.1.1071"
---

# Snapshot Hunter


The Snapshot Hunter is a Veeam technology used to detect and remove orphaned snapshots that may remain after backup or replication job sessions.

The Snapshot Hunter addresses the problem of “phantom” snapshots. Under some circumstances, VMware vSphere can report a successful removal of a snapshot, but the snapshot actually remains on the datastore.

Phantom snapshots can take substantial space on the datastore or impact VM performance. They can even cause the production VMs to stop if the datastore runs out of free space.

To solve the problem of phantom snapshots, Veeam Backup & Replication starts the Snapshot Hunter during each backup or replication job session. The Snapshot Hunter looks for snapshot files not registered in vSphere. If there are no orphaned files, the Snapshot Hunter stops. If orphaned snapshot files are detected, the Snapshot Hunter removes them in the background mode.

The Snapshot Hunter runs in jobs that use VMware VM snapshots:

* Backup jobs: regular backup and backup from storage snapshots
* Replication jobs (the source VM snapshot): regular replication, replication from storage snapshots
* VeeamZIP

|  |
| --- |
| Note |
| During Snapshot Hunter analysis, Veeam Backup & Replication skips VMware Cloud Director VMs. |

Related Topics

[How Snapshot Hunter Works](snapshot_hunter_hiw.md)


