---
title: "Restoring from Storage Snapshot"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_from_snapshot.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from Storage Snapshot


When you restore InterSystems IRIS instance data from a storage snapshot, Veeam Backup & Replication creates a thin clone of the selected snapshot on the source storage system through the Universal Storage API and mounts it directly to the target ODB server. No data is retrieved from a backup repository. This restore path is available when the backup policy is configured to retain storage snapshots.

|  |
| --- |
| NOTE |
| Before you start the restore wizard, create an auxiliary host for the LUN mount in the storage system interface, using any name except the vim aux prefix. If you do not, Veeam Backup & Replication creates this host automatically with the vim aux prefix and deletes all hosts that have this prefix when the storage system is removed from the Veeam Backup & Replication infrastructure, which can break the link between the target host and its volumes. |

Restore Destination

You can specify where to restore InterSystems IRIS instance data from snapshots created with the InterSystems IRIS plug-in in Veeam Backup & Replication.

* Original location — Veeam Backup & Replication restores the data to the same ODB server and path from which the backup was created. For details, see [Restoring to Original Location](iris_restore_snapshot_original_location.md).
* Different location — Veeam Backup & Replication restores the data to a different ODB server or a different target path. Specify the target server connection parameters and credentials. Use path mapping to set the target path for each source volume. For details, see [Restoring to a Different Location](iris_restore_snapshot_different_location.md).

For information about the steps that Veeam Backup & Replication performs automatically, see [Data Restore](iris_data_restore.md).

Page updated 2026-07-29

