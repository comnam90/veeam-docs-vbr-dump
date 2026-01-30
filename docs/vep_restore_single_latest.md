---
title: "Restoring Latest State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_single_latest.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Restoring Latest State


To restore the latest state of a PostgreSQL instance, do the following:

1. In the navigation pane, select a PostgreSQL instance you want to restore.
2. On the Instance tab, select Restore Instance > Restore latest state to <original\_location>.

Alternatively, you can right-click an instance and select Restore instance > Restore latest state to <original\_location>.

|  |
| --- |
| Note |
| The name of the restore option depends on the restore point you select during the [application item restore](restore_veeam_explorers.md) process in the Veeam Backup & Replication console.   * If you select the most recent available restore point, the option name is displayed as Restore latest state to <original\_location>. * If you select any other restore point, the option name is displayed as Restore state of <point\_in\_time> to <original\_location>. |

[![Restoring to Latest State](images/vep_restoring_latest.png)](images/vep_restoring_latest.png "Restoring to Latest State")


