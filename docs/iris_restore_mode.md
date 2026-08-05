---
title: "Step 3. Choose Restore Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_mode.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Choose Restore Mode


At the Restore Mode step of the wizard, specify where to restore the InterSystems IRIS instance data. Select the Restore to original location option to restore the data to the same ODB server from which the backup was created and write it to the same file system paths.

|  |
| --- |
| NOTE |
| Veeam Backup & Replication assumes that the file system paths on the target ODB server are identical to the paths recorded in the backup. If the paths have changed since the backup was created, select Restore to a different location and use path mapping to correct the discrepancy. For details, see [Restoring to Different Location](iris_restore_different_location.md). |

![Specify Restore Destination](images/iris_restore_disk_restore_mode.webp)

Page updated 2026-06-25

