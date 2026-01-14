---
title: "Exporting Latest State"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_rman_latest_state.html"
last_updated: "8/19/2025"
product_version: "13.0.1.1071"
---

# Exporting Latest State

In this article

To export a standalone database or Data Guard database as of the latest available state to the default location, do the following:

1. In the navigation pane, select a database.
2. On the Database tab, select Export as RMAN backup > Export latest state to Desktop\<db\_name>.

Alternatively, you can right-click a database and select Export as RMAN backup > Export latest state to Desktop\<db\_name>.

|  |
| --- |
| Note |
| The name of the export option depends on the restore point you select during the [application item restore](restore_veeam_explorers.md) process in the Veeam Backup & Replication console.   * If you select the most recent available restore point, the option name is displayed as Export latest state to Desktop\<db\_name>. * If you select any other restore point, the option name is displayed as Export state of <point\_in\_time> to Desktop\<db\_name>. |

Veeam Explorer for Oracle exports files in the following format: \_%I\_%d\_%T\_%U. For more information, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/21/rcmrf/formatSpec.html?source=%3Aso%3Atw%3Aor%3Aawr%3Aore%3A%3A%3Aautonmousblog#GUID-E51F637A-57E0-4B06-803F-3F879DF5BEED). To set a different export format, use [Exporting to Custom Location](veor_rman_custom_export.md).

[![Exporting Latest State](images/export_rman_latest_state.webp)](images/export_rman_latest_state.webp "Exporting Latest State")

After the export process is complete, review the results shown in the Database export summary window. To do this, click See more to expand the window and review details of the export operation.

You can filter notifications by their status: Error, Warning or Success.

[![Reviewing Export Summary Window](images/veor_export_summary.webp)](images/veor_export_summary.webp "Reviewing Export Summary Window")

Page updated 8/19/2025

Page content applies to build 13.0.1.1071
