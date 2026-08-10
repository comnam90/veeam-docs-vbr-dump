---
title: "Restoring Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_web_ui_single_pit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Point-in-Time State


You can restore a Microsoft SQL Server database as of a point-in-time state in your restore point.

The data will be restored in the following manner:

* Database files will be mounted to the original Microsoft SQL Server machine and copied to the original location.
* If a database with the same name already exists on a target Microsoft SQL Server machine, you will be prompted to overwrite the database with that from the backup file.

To restore SQL Server databases as of a point-in-time state, use the Restore wizard.

1. [Launch the Restore wizard](vesql_restore_web_ui_single_pit_wizard.md).
2. [Specify a restore point](vesql_restore_web_ui_single_pit_restore_point.md).
3. [Fine-tune the restore point](vesql_restore_web_ui_single_pit_fine_tune.md).
4. [Review the restore summary](vesql_restore_web_ui_single_pit_summary.md).

|  |
| --- |
| Note |
| Point-in-time restore is available only if transaction log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md). |

Page updated 2026-07-11

