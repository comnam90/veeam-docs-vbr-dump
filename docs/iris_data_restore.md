---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_data_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Restore


To recover InterSystems IRIS instance data, Veeam Backup & Replication provides a restore wizard. You can restore from a backup or from a storage snapshot, and you can restore to the original location or to a different server and path. Restore operations are orchestrated on the Veeam Backup & Replication server side. After Veeam Backup & Replication completes the automated steps, manual post-restore steps are required on the target ODB server to bring the InterSystems IRIS instance back online.

|  |
| --- |
| Important |
| Before you restore an InterSystems IRIS instance to its original location, you must manually stop the instance on the target ODB server. If the instance is running when the restore starts, the restore fails. |

|  |
| --- |
| NOTE |
| The restore wizard does not support recovery to a specific point in time. Because the backup policy does not process the journal (log) files of the InterSystems IRIS instance, you can restore only to the state captured in a full or incremental backup, or in a storage snapshot. For details, see [Backup Types](iris_backup_types.md). |

Restore from Backup

When you restore InterSystems IRIS instance data from a backup, Veeam Backup & Replication performs the following steps automatically:

1. Installs the required Veeam components on the target ODB server.
2. Creates the target folder if it does not exist.
3. Fetches the InterSystems IRIS instance data from the backup repository to the target. If the backup resides on a scale-out backup repository, data is read from the extents in parallel.

After Veeam Backup & Replication completes these steps, you must perform the required post-restore steps on the target ODB server to import the databases and start the instance. For the full restore procedure including post-restore steps, see [Restoring from Backup](iris_restore.md).

Restore from Storage Snapshot

When you restore InterSystems IRIS instance data from a storage snapshot, Veeam Backup & Replication creates a thin clone of the selected snapshot and mounts it directly to the target ODB server. No data is retrieved from a backup repository. This restore path is available only when the backup policy retains storage snapshots on the storage system.

Before you run the restore wizard, create an auxiliary host for the LUN mount in the storage system interface. Do not use the vim aux prefix in the host name. Veeam Backup & Replication reserves this prefix for hosts that it creates automatically and removes every host with this prefix when the storage system is removed from the Veeam Backup & Replication infrastructure. If such a host is removed, the link between the target ODB server and its volumes breaks and the restored instance becomes inaccessible.

|  |
| --- |
| Important |
| If you remove the storage system from Veeam Backup & Replication, the InterSystems IRIS restore points that are based on its storage snapshots become unavailable for restore, and volumes that have already been restored may be deleted from the storage system. |

When you restore from a storage snapshot, Veeam Backup & Replication performs the following steps automatically:

1. Installs the required Veeam components on the target ODB server.
2. Creates a thin clone of the selected snapshot through the Universal Storage API.
3. Exports the clone to the target ODB server through the Universal Storage API.
4. Mounts the LUN and its file system on the target.

After Veeam Backup & Replication completes these steps, you must perform the required post-restore steps on the target ODB server. For the full restore procedure including post-restore steps, see [Restoring from Storage Snapshot](iris_restore_from_snapshot.md).

Page updated 2026-07-29

