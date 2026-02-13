---
title: "Restoring Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restoring_multiple_pit.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Restoring Point-in-Time State


When restoring multiple databases, consider that depending on the database recovery model the following cases are possible:

* Some databases may be restored as of the different time interval.
* Some databases cannot be restored if there are no transaction logs available for the specified period.

To restore Microsoft SQL Server databases as of the point-in-time state, use the Restore wizard.

1. [Launch the Restore wizard](vesql_restoring_multiple_wizard_pit.md).
2. [Select databases you want to restore](vesql_restore_select_databases_multiple_pit.md).
3. [Specify a restore point](vesql_restoring_multiple_specify_restore_point_pit.md).
4. [Review the restore summary](vesql_restore_multiple_pit_summary.md).

|  |
| --- |
| Note |
| Point-in-time restore is available only if transaction log backups exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md). |


