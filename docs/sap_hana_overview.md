---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_hana_overview.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Overview


Veeam Plug-In for SAP HANA connects SAP HANA servers and Veeam backup repositories by interacting with databases through the SAP HANA Backint component. Backint for SAP HANA is the backup interface that enables Veeam Plug-In to communicate with SAP HANA databases and send the database backup files to the specified Veeam repositories. For details, see [How Veeam Plug-In for SAP HANA Works](hiw_sap_hana_plugin.md).

Veeam Plug-In for SAP HANA can operate in standalone or managed mode. Depending on the operation mode, Veeam Plug-In has different functionality and limitations. In standalone mode, you can install Veeam Plug-In manually on the computer whose databases you want to protect. Veeam Plug-In in standalone mode uses the Veeam Backup & Replication console to perform backup operations. In managed mode, you can install Veeam Plug-In using the Veeam Backup & Replication console. The Veeam Backup & Replication console automates the operation of Veeam Plug-Ins running on computers in your infrastructure. For details on Veeam Plug-In operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes).

Veeam Plug-In for SAP HANA transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups. You can use SAP HANA tools or the Veeam Backup & Replication console to initiate and manage backup operations. Backup processes are performed by the SAP HANA Backint tool. For details on backup operations with Veeam Plug-In, see [Data Backup](sap_hana_data_backup.md).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. You can use SAP HANA tools or the Veeam Backup & Replication console and Veeam Explorer for SAP HANA to initiate and manage restore operations. Restore processes managed with SAP HANA tools run on the SAP HANA side. Restore processes managed in the Veeam Backup & Replication console or in Veeam Explorer for SAP HANA run on the Veeam Backup & Replication side. For details on restore operations with Veeam Plug-In, see [Data Restore](sap_hana_data_restore.md).


