---
title: "Step 7. Specify Recovery State"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_recovery_state_single.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# Step 7. Specify Recovery State

In this article

At this step of the wizard, select a recovery state for the database.

1. Choose a recovery state:

* Default (RECOVERY)

Rolls back (undo) any uncommitted changes.

* NORECOVERY

Skips the undo phase so that uncommitted or incomplete transactions are held open.

This allows further restore stages to carry on from the restore point. When applying this option, the database will be in a norecovery state and inaccessible to users.

* STANDBY

The database will be in standby state and therefore available for read operations. You can also provide a standby file with uncommitted transactions.

1. Click Restore.

For more information on recovery states, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-database-options-page?view=sql-server-ver16#recovery-state).

|  |
| --- |
| Note |
| This step is unavailable if the Add the database to the following group check box is selected at the [Specify Always ON Restore Options](vesql_always_on_single.md) step. |

[![Specifying Recovery State](images/recovery_mode.webp)](images/recovery_mode.webp "Specifying Recovery State")

Page updated 11/12/2025

Page content applies to build 13.0.1.1071
