---
title: "Step 3. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_instant_multiple_point.html"
last_updated: "8/24/2025"
product_version: "13.0.1.1071"
---

# Step 3. Specify Restore Point


At this step of the Instant Recovery wizard, select a state as of which you want to recover databases:

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created.

* Select the Restore to a specific point in time option to load database files as of the selected point in time. Note that this option is available only if archived log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

Use the slider to choose the point in time you need.

If some of the databases do not have transaction log backups for the specified time, they will be displayed below with their own time point.

[![Specifying Restore Point](images/instant_multiple_point_vesql.webp)](images/instant_multiple_point_vesql.webp "Specifying Restore Point")


