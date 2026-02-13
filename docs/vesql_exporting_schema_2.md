---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_exporting_schema_2.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the wizard, select a state as of which you want to export your data:

* Select the Restore to the point in time of the selected image-level backup option to load data as of the moment when the current restore point was created.

* Select the Restore to a specific point in time option to load data as of the selected point in time. Note that this option is available only if transaction log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

Use the slider to choose the point in time you need.

* Select the Perform restore to the specific transaction check box to load data exactly as of the moment before undesired transactions.

|  |
| --- |
| Note |
| The Perform restore to the specific transaction option requires a staging SQL server. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md). |

![Step 2. Specify Restore Point](images/export_point.webp "Specifying Restore Point")


