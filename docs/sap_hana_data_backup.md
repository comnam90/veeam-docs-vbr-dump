---
title: "Data Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_hana_data_backup.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Data Backup

In this article

Veeam Plug-In for SAP HANA transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups.

You can use the SAP HANA tools or the Veeam Backup & Replication console to initiate and manage backup operations. With the SAP HANA tools, you can schedule and delete backups, configure backup settings, and back up SAP HANA databases. The SAP HANA Backint tool performs all initiated backup processes on the SAP HANA side.

For each backup operation, Veeam Plug-In automatically creates and stores database backup files. For each of the created backup files, Veeam Plug-In also creates separate metadata files. The backup and metadata files help Veeam Plug-Ins to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup jobs reside in a dedicated job folder in the backup repository. For details on backup files, see [Veeam Plug-In Backup Files](saphana_bfiles.md).

To store backup files, you can add backup repositories to your Veeam Backup & Replication infrastructure. For details on all supported backup repositories, see [Veeam Backup Repositories](sap_repos.md).

For details on how to use the specific backup tools, see [Database Protection](sap_hana_backup.md).

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
