---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_ir_single_pit_specify_restore_point.html"
last_updated: "2/13/2026"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the Instant Recovery wizard, select a state as of which you want to restore your database:

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created.

* Select the Restore to a specific point in time option to load database files as of the selected point in time. Use the slider to choose the point in time you need.

* Select the Perform restore to the specific transaction check box to load database files exactly as of the moment before undesired transactions.

|  |
| --- |
| Note |
| The Perform restore to the specific transaction option requires a staging Oracle server. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md). |

![Step 2. Specify Restore Point](images/instant_restore_point.webp "Specifying Restore Point")


