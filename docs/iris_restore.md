---
title: "Restoring from Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from Backup


When you restore InterSystems IRIS instance data from a backup, Veeam Backup & Replication retrieves the backup data from the backup repository and writes it to the target ODB server. This restore path is available when the backup policy runs in backup mode and backup files exist in the repository. After Veeam Backup & Replication completes the data transfer, you must perform manual steps on the target ODB server to bring the InterSystems IRIS instance back online.

Restore Destination

You can specify where to restore InterSystems IRIS instance data from application backup policies created with the InterSystems IRIS plug-in in Veeam Backup & Replication.

* Original location — Veeam Backup & Replication restores the data to the same ODB server and the same paths from which the backup was created. For details, see [Restoring to Original Location](iris_restore_original_location.md).
* Different location — Veeam Backup & Replication restores the data to a different ODB server or a different path. Specify the target server connection parameters and credentials. Use path mapping to set the target path for each source volume. For details, see [Restoring to Different Location](iris_restore_different_location.md).

For details about the steps that Veeam Backup & Replication performs automatically during the restore, see [Data Restore](iris_data_restore.md).

Page updated 2026-06-25

