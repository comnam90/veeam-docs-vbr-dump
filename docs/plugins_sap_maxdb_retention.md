---
title: "Retention of SAP MaxDB Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retention of SAP MaxDB Backups


To set an automatic removal of old backups, you can use the retention policy of Veeam Plug-In for SAP MaxDB.

The --set-force-delete command of Veeam Plug-In automatically deletes backup files which are older than specified number of days. For details, see [Configuring Retention Policy for Backups](plugins_sap_maxdb_retention_garbage_collector.md).

Also, you can manually manage backups from a backup repository using the Veeam Backup & Replication console. For details, see [Deleting Backups Manually](manual_remove.md) and [Removing Backups from Configuration](plugins_sap_maxdb_retention_garbage_collector_remove_from_config.md).

Page updated 2026-08-04

