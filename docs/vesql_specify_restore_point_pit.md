---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_specify_restore_point_pit.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the wizard, specify a state to which you want to restore your database:

1. In the Specify point in time you want to restore the database to section, select one of the following options:

* Restore to the point in time of the selected image-level backup. Select this option to load database files as of the moment when the current restore point was created.
* Restore to a specific point in time. Select this option to load database files as of the selected point in time. Use the slider to choose the point in time you need.

This option is available in case the following conditions are met:

* [For restore from a backup created by a backup job] The backup is created by a job that is set to back up transaction logs or process transaction logs in the copy only mode.
* [For restore from a backup created by a backup copy job] The backup is created by a job that is set to process transaction logs.

* The recovery model for the database is set to full or bulk-logged.

1. [Optional] Select the Perform restore to the specific transaction check box to load database files exactly as of the moment before undesired transactions. If you select this option, you will be able to specify an exact transaction at the [next step](vesql_fine_tune_pit.md) of the wizard.

This option requires a staging Microsoft SQL Server. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md).

This option is unavailable when restoring multiple databases.

![Step 2. Specify Restore Point](images/restore_point.webp "Specifying Restore Point")


