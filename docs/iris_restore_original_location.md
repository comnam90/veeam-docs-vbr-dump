---
title: "Restoring to Original Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_original_location.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring to Original Location


When you restore InterSystems IRIS instance data to the original location, Veeam Backup & Replication writes the data back to the same ODB server and the same file system paths from which the backup was created. No path mapping or additional credentials are required. Veeam Backup & Replication uses the connection established during protection group setup.

|  |
| --- |
| Important |
| Stop the InterSystems IRIS instance on the ODB server before starting the restore wizard. If the instance is still running when Veeam Backup & Replication attempts to overwrite the .DAT files, the restore will fail. |

To restore InterSystems IRIS instance data to the original location, you can perform the following operations:

1. [Launch the InterSystems IRIS Instance Restore wizard](iris_restore_launch.md).
2. [Select a restore point](iris_restore_point.md).
3. [Specify a restore destination](iris_restore_mode.md).
4. [Specify the restore operation reason](iris_restore_reason.md).
5. [Complete the restore process](iris_restore_summary.md).
6. [Perform post-restore operations](iris_restore_post.md).

Page updated 2026-06-25

