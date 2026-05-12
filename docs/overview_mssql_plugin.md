---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/overview_mssql_plugin.html"
last_updated: "5/11/2026"
product_version: "13.0.1.2067"
---

# Overview


Veeam Plug-In for Microsoft SQL Server integrates Microsoft SQL Server and Veeam Backup & Replication to manage database backup and restore operations. When configured, Veeam Plug-In for Microsoft SQL Server allows Microsoft SQL Server to perform backup operations and store backups directly on Veeam Backup & Replication backup repositories. For details, see [How Veeam Plug-In for Microsoft SQL Server Works](hiw_mssql_plugin.md).

Integrating Microsoft SQL Server and Veeam Backup & Replication enables Veeam Plug-In to use native Microsoft SQL Server backup features while using Veeam Backup & Replication backup management and storage capabilities. You can perform full, differential and transaction log backup operations using the Microsoft SQL Server Management Studio. You can use Microsoft SQL Server Management Studio to initiate backup operations and manage stored backups. Use the Veeam Backup & Replication console only to view backup operation processes and create backup job reports. For details, see [Data Backup](data_backup_mssql_plugin.md).

Veeam Plug-In for Microsoft SQL Server can operate in standalone or managed mode. Depending on the operation mode, Veeam Plug-In has different functionality and limitations. In standalone mode, you can install Veeam Plug-In manually on the computer whose databases you want to protect. Veeam Plug-In in standalone mode uses the Veeam Backup & Replication console to perform backup operations. In managed mode, you can install Veeam Plug-In using the Veeam Backup & Replication console. The Veeam Backup & Replication console automates the operation of Veeam Plug-Ins running on computers in your infrastructure. To learn more about Veeam Plug-In operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. You can restore entire databases from a full backup or to a specific point in time, based on transaction logs. Veeam Plug-In for Microsoft SQL Server supports restoring databases to the original Microsoft SQL Server machine or another server. For details, see [Data Restore](data_restore_mssql_plugin.md).


