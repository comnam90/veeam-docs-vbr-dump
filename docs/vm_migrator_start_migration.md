---
title: "Step 7. Start Migration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_start_migration.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Step 7. Start Migration


The utility performs migration according to the migration task file. To start the migration, run the Start-VBRViVMMigration cmdlet and specify the File parameter value.

|  |
| --- |
| Start-VBRViVMMigration -File C:\Folder\vcenter70\_old\_to\_vcenter70\_migration\_task |

This operation will update Veeam Backup & Replication database. If you encounter issues after migration, perform the restore of Veeam Backup & Replication configuration database. For more information, see [Restoring Configuration Database](vbr_config_restore_linux.md).


