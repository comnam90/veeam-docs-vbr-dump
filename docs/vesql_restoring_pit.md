---
title: "Restoring Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restoring_pit.html"
last_updated: "9/26/2024"
product_version: "13.0.1.1071"
---

# Restoring Point-in-Time State


You can restore a Microsoft SQL Server database as of a point-in-time state in your backup file.

The data will be restored in the following manner:

* Database files will be copied to the original location and then mounted to the original Microsoft SQL Server.
* If a database with the same name already exists on a target Microsoft SQL Server, it will be replaced with the database from a backup file.

To restore SQL Server databases as of a point-in-time state, use the Restore wizard.

1. [Launch the Restore wizard](vesql_wizard_pit.md).
2. [Specify a restore point](vesql_specify_restore_point_pit.md).
3. [Fine-tune the restore point](vesql_fine_tune_pit.md).
4. [Review the restore summary](vesql_restore_single_pit_summary.md).


