---
title: "Restoring Latest State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_databases_single_latest.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Latest State


To restore the latest state of a PostgreSQL database, do the following:

1. In the navigation pane, select a PostgreSQL database you want to restore.
2. On the Database tab, select Restore Database > Restore latest state to <original\_location>.

Alternatively, you can right-click a database and select Restore Database > Restore latest state to <original\_location>.

|  |
| --- |
| Note |
| The name of the restore option depends on the restore point you select during the [application item restore](restore_veeam_explorers.md) process in the Veeam Backup & Replication console.   * If you select the most recent available restore point, the option name is displayed as Restore latest state to <original\_location>. * If you select any other restore point, the option name is displayed as Restore state of <point\_in\_time> to <original\_location>. |

Note that if a database with the same name exists on the server, you will be prompted to overwrite it.

[![Restoring to Latest State](images/vep_restoring_latest_database.webp)](images/vep_restoring_latest_database.webp "Restoring to Latest State")

Page updated 2026-07-29

