---
title: "Exporting Latest State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_df_latest_state.html"
last_updated: "8/19/2025"
product_version: "13.0.1.1071"
---

# Exporting Latest State


To export a standalone database or Data Guard database as of the latest available state to the default location, do the following:

1. In the navigation pane, select a database.
2. On the Database tab, select Export Database Files > Export latest state to Desktop\<db\_name>.

Alternatively, you can right-click a database and select Export database files > Export latest state to Desktop\<db\_name>.

|  |
| --- |
| Note |
| The name of the export option depends on the restore point you select during the [application item restore](restore_veeam_explorers.md) process in the Veeam Backup & Replication console.   * If you select the most recent available restore point, the option name is displayed as Export latest state to Desktop\<db\_name>. * If you select any other restore point, the option name is displayed as Export state of <point\_in\_time> to Desktop\<db\_name>. |

[![Exporting Latest State](images/df_latest_export.webp)](images/df_latest_export.webp "Exporting Latest State")

After the export process is complete, review the results shown in the Database export summary window. To do this, click See more to expand the window and review details of the export operation.

You can filter notifications by their status: Error, Warning or Success.

[![Reviewing Export Summary Window](images/veor_export_summary.webp)](images/veor_export_summary.webp "Reviewing Export Summary Window")


