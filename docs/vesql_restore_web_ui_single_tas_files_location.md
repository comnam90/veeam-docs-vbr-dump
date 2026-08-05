---
title: "Step 6. Specify Files Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_web_ui_single_tas_files_location.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify Files Location


At the Database Files step, specify the following file locations.

* Primary database file
* Secondary database and log files
* BLOB stores (if necessary)

|  |
| --- |
| Note |
| Make sure the account you are using has Read and Write permissions. |

To specify a file location, do the following:

1. Click Browse next to the necessary database file type.

[![Specifying Files Location](images/vesql_restore_web_ui_single_tas_files_location_location.webp)](images/vesql_restore_web_ui_single_tas_files_location_location.webp "Specifying Files Location")

1. In the Browse window, select a database file or folder for the restored database and click OK. To create a new folder, click New Folder.

[For restore to another location] To prevent you from storing BLOBs from different databases in the same directory, Veeam Explorer for Microsoft SQL Server supports creating a BLOB stores folder using the Restore wizard only. If you select an already existing folder, Veeam Explorer for Microsoft SQL Server will display an error.

[![Selecting File](images/vesql_restore_web_ui_single_tas_files_location_select_file.webp)](images/vesql_restore_web_ui_single_tas_files_location_select_file.webp "Selecting File")

Page updated 2026-07-07

