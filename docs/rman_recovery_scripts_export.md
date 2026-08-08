---
title: "Recovery Script Export"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_recovery_scripts_export.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Recovery Script Export


Recovery script export allows you to quickly generate RMAN recovery scripts as separate files instead of running the restore operation.

This feature is intended to assist with manual RMAN restore and for situations where the backup administrator does not have authentication credentials for the target Oracle server — for example, if they have no access to the identity provider that manages authentication to the server. Once you generate the scripts, you can share them with authorized database administrators.

Note that the exported recovery scripts include the core Veeam Explorer for Oracle commands, with details for the selected backup, such as DBID, backup piece names, SBT library path, and Veeam Plug-In for Oracle RMAN parameters. They do not replace the full restore workflow or cover all RMAN scenarios.

When using the exported scripts, the database administrators must perform all required RMAN preparations, recovery steps and post-restore actions manually on the target server.

The recovery script export operation generates one or three scripts depending on the selected restore options. For more information, see [Specify Export Location](rman_export_specify_export_location.md).

For more information on how to run the scripts on the target Oracle server, see [Database Recovery](oracle_db_restore.md).

|  |
| --- |
| Note |
| Consider the following:   * This wizard does not connect to the target Oracle server. For this reason, it omits the target server and password steps of the Restore wizard. * When you run the recovery scripts, Veeam Plug-In for Oracle RMAN must be installed on the target server and must be able to access the backup. * Note that the exported scripts may contain placeholders. The database adinistrator should proofread the scripts and make sure that their contents match the Oracle environment on the target server. |

To export recovery scripts for the selected database, do the following:

1. [Launch the Export wizard](rman_export_wizard.md).
2. [Specify the recovery type](rman_export_specify_recovery_type.md).
3. [Specify Oracle settings](rman_export_specify_oracle_settings.md).
4. [Specify point in time](rman_export_specify_pit.md).
5. [Specify database files location](rman_export_specify_file_location.md).
6. [Configure channel allocation](rman_export_configure_channel_allocation.md).
7. [Specify the export location](rman_export_specify_export_location.md).
8. [Review the export summary](veor_export_rman_summary.md).

Page updated 2026-07-24

