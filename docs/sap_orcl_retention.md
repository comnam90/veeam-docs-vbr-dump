---
title: "Retention of SAP on Oracle Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_retention.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Retention of SAP on Oracle Backups


To set an automatic removal of old backups, you can use the retention policy of Veeam Plug-In for SAP on Oracle. The --set-force-delete command of Veeam Plug-In automatically deletes backup files which are older than specified number of days. For details, see [Configuring Retention Policy for Backups](garbage_collector_sap_orcl.md).

Also, you can manually delete backups from a backup repository using the Veeam Backup & Replication console. For details, see [Deleting Backups Manually Using Veeam Backup & Replication Console](manual_remove.md).


