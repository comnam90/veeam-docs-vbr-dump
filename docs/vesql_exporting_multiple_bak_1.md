---
title: "Step 3. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_exporting_multiple_bak_1.html"
last_updated: "9/7/2023"
product_version: "13.0.1.1071"
---

# Step 3. Specify Restore Point


At this step of the wizard, select a state as of which you want to restore your database:

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created by the backup or replication job.

* Select the Restore to a specific point in time option to load database files as of the specified point in time.

Use the slider to choose the point in time you need.

|  |
| --- |
| Note |
| The Perform restore to the specific transaction option is unavailable when exporting multiple databases. |

[![Specifying Restore Point](images/export_mult_different.webp)](images/export_mult_different.webp "Specifying Restore Point")


