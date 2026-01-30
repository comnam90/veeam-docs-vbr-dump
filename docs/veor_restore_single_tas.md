---
title: "Restoring to Another Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_restore_single_tas.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Restoring to Another Server


This section explains how to restore a standalone database and Data Guard database to another server.

|  |
| --- |
| Note |
| When restoring from a Data Guard to another server as described in this section, the databases from the Data Guard will be restored as standalone Oracle databases, preserving no Data Guard infrastructure. To restore Data Guard infrastructure altogether, use either latest state restore, or point-in-time restore. For more information, see [Restoring Latest State](veor_restore_single_latest.md) and [Restoring Point-in-Time State](veor_restore_single_pit.md). |

To restore data, take the following steps:

1. [Launch the Restore wizard](veor_restore_single_tas_wizard.md).
2. [Specify a restore point](veor_restore_single_tas_specify_restore_point.md).
3. [Fine-tune the restore point](veor_restore_single_tas_fine_tune.md).
4. [Specify the target server](veor_restore_single_tas_specify_target_server.md).
5. [Specify Oracle settings](veor_restore_single_tas_specify_oracle_settings.md).
6. [Specify database files location](veor_restore_single_tas_specify_database_location.md).
7. [Review the restore summary](veor_restore_single_tas_summary.md).


