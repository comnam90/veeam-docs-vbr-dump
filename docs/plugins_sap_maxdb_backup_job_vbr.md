---
title: "Backup Job in Veeam Backup & Replication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_job_vbr.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Backup Job in Veeam Backup & Replication

In this article

After Veeam Plug-In for SAP MaxDB starts the backup process, Veeam Backup & Replication creates the backup job. You can use this job to view statistics on the backup process and generate backup job reports. You can also disable or delete the backup job.

Consider the following:

* You cannot start or edit Veeam Plug-In backup jobs in the Veeam Backup & Replication console. You can manage backup operations on the machine with Veeam Plug-In only.
* Veeam Backup & Replication creates one backup job for a machine with Veeam Plug-In for SAP MaxDB. All backup sessions for different databases that reside on this machine run within this backup job.
* Veeam Backup & Replication generates names for SAP MaxDB backup jobs according to the names of the machine with Veeam Plug-In and selected backup repository.

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](plugins_sap_maxdb_backup_job_vbr_statistics.md)
* [Generate a backup job report](plugins_sap_maxdb_backup_job_vbr_reports.md)
* [Disable a backup job](plugins_sap_maxdb_backup_job_vbr_disable.md)
* [Delete a backup job](plugins_sap_maxdb_backup_job_vbr_delete.md)

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
