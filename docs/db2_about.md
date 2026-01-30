---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_about.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Overview


Veeam Plug-In for IBM Db2 uses the backup and restore functionality of IBM Db2 built-in tools and transfers backups to Veeam backup repositories. For details, see [How Veeam Plug-In for IBM Db2 Works](db2_hiw.md).

With the configured Veeam Plug-In, you can perform full, incremental or log backups for IBM Db2 databases. Use Veeam Plug-In to back up databases in the following cases:

* If you want the database administrator to fully control the backup and recovery processes.
* If you want to back up and restore individual databases.
* If you want to use existing scripts or external schedulers.
* If you use high availability disaster recovery (HADR).

You can use the Veeam Backup & Replication console to initiate and manage the Veeam Plug-In backup operations. For details, see [Data Backup](db2_data_backup.md).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. You can restore entire databases from a full backup or to a specific point in time. Veeam Plug-In for IBM Db2 supports restoring databases to the original IBM Db2 machine or another server. For details, see [Data Restore](db2_data_restore.md).


