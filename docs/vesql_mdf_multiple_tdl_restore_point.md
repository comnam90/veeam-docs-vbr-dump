---
title: "Step 3. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_mdf_multiple_tdl_restore_point.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 3. Specify Restore Point


At this step of the wizard, select a state as of which you want to export your databases:

* Select the Restore to the point in time of the selected image-level backup option to load data as of the moment when the current restore point was created by the backup or replication job.

* Select the Restore to a specific point in time option to load data as of the specified point in time. Note that this option is available only if transaction log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

Use the slider to choose the point in time you need.

|  |
| --- |
| Note |
| The Perform restore to the specific transaction option is unavailable when exporting multiple databases. |

![Step 3. Specify Restore Point](images/export_mult_different.webp "Specifying Restore Point")


