---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_instant_restore_point.html"
last_updated: "8/24/2025"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the Instant Recovery wizard, select a state as of which you want to restore your database:

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created.

* Select the Restore to a specific point in time option to load database files as of the selected point in time. Note that this option is available only if archived log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

1. Use the slider to choose the point in time you need.
2. If you want to load database files exactly as of the moment before undesired transactions, select the Perform restore to the specific transaction check box. Note that this option requires a staging server where Microsoft SQL Server is deployed. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md).

[![Specifying Restore Point](images/instant_another_point.webp)](images/instant_another_point.webp "Specifying Restore Point")


