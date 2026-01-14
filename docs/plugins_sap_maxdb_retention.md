---
title: "Retention of SAP MaxDB Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_retention.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Retention of SAP MaxDB Backups

In this article

To set an automatic removal of old backups, you can use the retention policy of Veeam Plug-In for SAP MaxDB.

The --set-force-delete command of Veeam Plug-In automatically deletes backup files which are older than specified number of days. For details, see [Configuring Retention Policy for Backups](garbage_collector_sap_orcl.md).

Also, you can manually manage backups from a backup repository using the Veeam Backup & Replication console. For details, see [Deleting Backups Manually](manual_remove.md) and [Removing Backups from Configuration](plugins_sap_maxdb_retention_garbage_collector_remove_from_config.md).

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
