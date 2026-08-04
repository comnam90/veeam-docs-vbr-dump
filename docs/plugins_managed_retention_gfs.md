---
title: "Long-Term Retention Policy (GFS)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_managed_retention_gfs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Long-Term Retention Policy (GFS)


The long-term or Grandfather-Father-Son (GFS) retention policy allows you to store backup files for long periods of time — for weeks, months and years. The GFS retention is available only for the following Veeam Plug-Ins operating in the managed mode:

* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP HANA
* Veeam Plug-In for Microsoft SQL Server

Veeam Plug-In for SAP on Oracle does not support the GFS retention policy.

How GFS Retention Works

The GFS retention for backups created with Veeam Plug-Ins works as follows:

1. Once you configure the GFS retention policy as part of the application backup policy, Veeam Backup & Replication sends this information to Veeam Plug-In.
2. Veeam Plug-In pings Veeam Backup & Replication before creating a full backup.
3. Veeam Backup & Replication checks the GFS schedule and decides whether it is necessary to assign a GFS flag to the full backup that Veeam Plug-In is about to create.
4. If Veeam Backup & Replication assigns a GFS flag to the full backup file, the created .VAB file contains only one full backup and is closed immediately after backup completion. This backup file can no longer be deleted, modified or reused. The short-term retention policy ignores GFS-flagged backups and does not delete them. As a result, Veeam Backup & Replication achieves immediate immutability of the backup.

Veeam Backup & Replication can assign the following types of GFS flags: weekly (W), monthly (M) and yearly (Y). A single full backup file can carry several flags at once.

1. On the day when the GFS period expires, Veeam Backup & Replication removes the flag from the file. If a file carries several flags, Veeam Backup & Replication removes each flag separately as the dedicated period ends. As a result, Veeam Backup & Replication deletes a file only after all GFS flags are removed.

Related Topics

* [Configure Long-Term Retention for the Oracle RMAN Backup Policy](policy_oracle_rman_gfs.md)
* [Configure Long-Term Retention for the SAP HANA Backup Policy](policy_sap_hana_gfs.md)
* [Configure Long-Term Retention for the Microsoft SQL Server Backup Policy](policy_microsoft_sql_server_gfs.md)

Page updated 2026-07-24

