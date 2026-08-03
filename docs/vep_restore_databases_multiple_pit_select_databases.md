---
title: "Step 2. Select Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_databases_multiple_pit_select_databases.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Databases


At this step of the wizard, select the databases that you want to restore.

To quickly find the necessary databases, use the search field or sort the databases by name. If the databases belong to multiple instances, you can also sort the databases by instance name.

|  |
| --- |
| Note |
| Veeam Explorer for PostgreSQL restores data to the same data directories and tablespace directories as on the backup file. If any of the target data or tablespace directories are not empty, you will be prompted to overwrite them. |

![Step 2. Select Databases](images/vep_restore_select_databases.webp "Selecting Databases to Restore")

Page updated 2026-07-29

