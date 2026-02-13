---
title: "Exporting Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_df_pit.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Exporting Point-in-Time State


This section explains how to export a standalone database or a Data Guard database as database files to a selected point-in-time state on the backup file. Your Oracle data will be restored to the default location.

To export database files as of a point-in-time state, do the following:

1. [Launch the Export wizard](veor_df_export_wizard_pit.md).
2. [Specify a restore point](veor_df_export_srp.md).
3. [Fine-tune the restore point](veor_df_export_frp.md).
4. [Review the export summary](veor_export_dbfiles_pit_summary.md).

|  |
| --- |
| Note |
| Point-in-time restore is available only if archived log backups exist. For more information, see [Required Job Settings](veo_bu_job_settings.md). |


