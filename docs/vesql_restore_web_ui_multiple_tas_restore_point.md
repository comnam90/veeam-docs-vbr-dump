---
title: "Step 3. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_web_ui_multiple_tas_restore_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Restore Point


At the Restore Point step, select a state as of which you want to restore your database:

* Select the Selected restore point option to load database files as of the moment when the current restore point was created.

* Select the Specific point in time option to load database files as of the specified point in time. Use the slider to choose the point in time you need.

Note that this option is available only if transaction log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

If the backed-up transaction logs do not contain information about some databases for the selected point in time, those databases will be recovered as of their latest available state.

[![Specifying Restore Point](images/vesql_restore_web_ui_multiple_tas_restore_point.webp)](images/vesql_restore_web_ui_multiple_tas_restore_point.webp "Specifying Restore Point")

Page updated 2026-07-07

