---
title: "Overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_overview.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Overview

In this article

Veeam Plug-In for SAP on Oracle functions as an agent between SAP BR\*Tools and Veeam backup repositories. With the configured Veeam Plug-In, you can use the SAP BR\*Tools to perform backup and restore operations. Veeam Plug-In compresses and transfers database backups to a backup repository connected to Veeam Backup & Replication. To learn more, see [How Veeam Plug-In for SAP on Oracle Works](hiw_sap_orcl_plugin.md).

Veeam Plug-In for SAP on Oracle can operate in standalone or managed mode. Depending on the operation mode, Veeam Plug-In has different functionality and limitations. In standalone mode, you can install Veeam Plug-In manually on the computer whose databases you want to protect. Veeam Plug-In in standalone mode uses the Veeam Backup & Replication console to perform backup operations. In managed mode, you can install Veeam Plug-In using the Veeam Backup & Replication console. The Veeam Backup & Replication console automates the operation of Veeam Plug-Ins running on computers in your infrastructure. To learn more about Veeam Plug-In operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes).

For backup operations, use the SAP BR\*Tools. Veeam Plug-In for SAP on Oracle transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups. To learn more about backup operations, see [Data Backup](sap_orcl_data_backup.md).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. All restore operations are performed on the SAP BR\*Tools side. To learn more about restore operations with Veeam Plug-In, see [Data Restore](sap_orcl_data_restore.md).

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
