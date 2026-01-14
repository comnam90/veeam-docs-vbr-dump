---
title: "Step 2. Specify Restore Point"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_point_schema.html"
last_updated: "4/10/2024"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point

In this article

At this step of the wizard, select a state as of which you want to restore your database:

* Select the Restore to the point in time of the selected image-level backup option to load database files as of the moment when the current restore point was created.

* Select the Restore to a specific point in time option to load database files as of the selected point in time.

Use the slider to choose the point in time you need.

* Select the Perform restore to the specific transaction check box to load database files exactly as of the moment before undesired transactions.

[![Specifying Restore Point](images/restore_point.webp)](images/restore_point.webp "Specifying Restore Point")

Page updated 4/10/2024

Page content applies to build 13.0.1.1071
