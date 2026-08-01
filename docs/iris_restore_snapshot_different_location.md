---
title: "Restoring to a Different Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_snapshot_different_location.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring to a Different Location


When you restore InterSystems IRIS instance data to a different location, Veeam Backup & Replication writes the data back to a different specified ODB server and creates new file system paths from which the backup was created. Additional path mapping and credentials for the different location server are required. Veeam Backup & Replication uses the connection established during protection group setup.

|  |
| --- |
| Important |
| Before starting the snapshot InterSystems IRIS instance restore, ensure the following conditions are met:   * The IRIS instance on the ODB server is stopped. * The restored volumes are unmounted from the target server and no longer in use.   If the instance is still running when Veeam Backup & Replication attempts to overwrite the .DAT files, the restore will fail. |

To restore InterSystems IRIS instance data to a different location, you can perform the following operations:

1. [Launch the InterSystems IRIS Instance Restore wizard](iris_restore_snapshot_different_location_launch.md).
2. [Select a restore point](iris_restore_snapshot_different_location_point.md).
3. [Specify a restore destination](iris_restore_snapshot_different_location_mode.md).
4. [Specify the new file path for restored files](iris_instance_restore_snapshot_path_map.md).
5. [Specify the restore operation reason](iris_restore_snapshot_different_location_reason.md).
6. [Complete the restore process](iris_restore_snapshot_different_location_summary.md).
7. [Perform post-restore operations on the target server](iris_restore_snapshot_different_location_post.md).

Page updated 2026-06-25

