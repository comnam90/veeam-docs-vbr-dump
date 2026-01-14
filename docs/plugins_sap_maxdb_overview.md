---
title: "Overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_overview.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Overview

In this article

Veeam Plug-In for SAP MaxDB uses the backup and restore functionality of SAP MaxDB built-in functionality and transfers backups to Veeam backup repositories. For details, see [How Veeam Plug-In for SAP MaxDB Works](plugins_sap_maxdb_overview_hiw.md).

With the configured Veeam Plug-In, you can perform full, incremental or log backups for SAP MaxDB databases. Use Veeam Plug-In to back up databases in the following cases:

* If you want the database administrator to fully control the backup and recovery processes.
* If you want to back up and restore individual databases.
* If you want to use existing scripts or external schedulers.

* If you use high availability disaster recovery (HADR).

You can install Veeam Plug-In manually on the computer whose databases you want to protect and use the Veeam Backup & Replication console to initiate and manage the Veeam Plug-In backup operations. For backup operations, use the SAP MaxDB functionality. Veeam Plug-In transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups. To learn more about backup operations, see [Data Backup](plugins_sap_maxdb_overview_backup.md).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. All restore operations are performed on the SAP MaxDB side. To learn more about restore operations with Veeam Plug-In, see [Data Restore](plugins_sap_maxdb_overview_data_restore.md).

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
