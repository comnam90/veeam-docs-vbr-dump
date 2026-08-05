---
title: "Step 3. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_databases_multiple_pit_specify_restore_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Restore Point


At this step of the wizard, select a state as of which you want to restore your data.

1. Choose a point-in-time state.

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created.
* Select the Restore to a specific point in time option to obtain database files as of the selected point in time within the available restore period. Use the slider to choose the point in time you need.

1. Click Restore.

|  |
| --- |
| Note |
| If the backed-up WAL files do not contain information about some databases for the selected point in time, those databases will be recovered as of their latest available state. |

![Step 3. Specify Restore Point](images/vep_point_in_time_specify_restore_point_database.webp "Specifying Restore Point")

Page updated 2026-07-20

