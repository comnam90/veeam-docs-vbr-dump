---
title: "Short-Term Retention Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_managed_retention_short.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Short-Term Retention Policy


The short-term retention policy allows you to store backup files for a limited period of time — for a number of days. The short-term retention policy is available for all Veeam Plug-Ins operating in the managed mode.

How Short-Term Retention Works

In the management scenario, Veeam Backup & Replication applies the short-term retention policy at the application policy level as follows:

1. By default, Veeam Backup & Replication keeps backup files for 7 days. You can configure another retention period in days during the application backup policy configuration.
2. After each backup session, Veeam Backup & Replication checks the age of restore points.
3. Veeam Backup & Replication removes the outdated restore points.

As Microsoft SQL Server creates backups in a backup chain, Veeam Backup & Replication removes outdated restore points created with Veeam Plug-In for Microsoft SQL Server only from the inactive part of the backup chain. Only after the last restore point in a backup chain becomes outdated, Veeam Backup & Replication removes the inactive backup chain.

The short-term retention policy does not remove backups created for the purpose of the long-term retention policy. For details, see [Long-Term Retention Policy (GFS)](plugins_managed_retention_gfs.md).

Related Topics

* [Storage Settings for the Oracle RMAN Backup Policy](policy_oracle_rman_repository.md)
* [Storage Settings for the SAP HANA Backup Policy](policy_sap_hana_repository.md)
* [Storage Settings for the SAP on Oracle Backup Policy](policy_sap_oracle_repository.md)
* [Storage Settings for the Microsoft SQL Server Backup Policy](policy_microsoft_sql_server_repository.md)

Page updated 2026-06-16

