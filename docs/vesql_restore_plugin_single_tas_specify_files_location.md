---
title: "Step 5. Specify Files Location"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_plugin_single_tas_specify_files_location.html"
last_updated: "9/23/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Files Location

In this article

At this step of the wizard, specify the following file locations.

* Primary database file
* Secondary database file and log files
* BLOB stores (if necessary)

|  |
| --- |
| Note |
| Make sure the account you are using has Read and Write permissions. |

To specify a file location, do the following:

1. Click Browse next to the necessary database file type.

[![Specifying Files Location](images/vesql_restore_plugin_single_tas_specify_files_location.webp)](images/vesql_restore_plugin_single_tas_specify_files_location.webp "Specifying Files Location")

1. In the Select File dialog, choose a database file or folder for the restored database and click Select. To create a new folder, click Create Folder.

[For restore to another location] To prevent you from storing BLOBs from different databases in the same directory, Veeam Explorer for Microsoft SQL Server supports creating a BLOB stores folder using the Restore wizard only. If you select an already existing folder, Veeam Explorer for Microsoft SQL Server will display an error.

[![Selecting File](images/select_file.webp)](images/select_file.webp "Selecting File")

Page updated 9/23/2025

Page content applies to build 13.0.1.1071
