---
title: "Managing Backup Jobs in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_job_vbr.html"
last_updated: "12/17/2024"
product_version: "13.0.1.1071"
---

# Managing Backup Jobs in Veeam Backup & Replication


After Veeam Plug-In for IBM Db2 starts the backup process, Veeam Backup & Replication creates the backup job. You can use this job to view statistics on the backup process and generate backup job reports. You can also disable or delete the backup job.

You cannot start or edit Veeam Plug-In backup jobs in the Veeam Backup & Replication console. You can manage backup operations on the machine with Veeam Plug-In only.

Consider the following:

* Veeam Backup & Replication creates one backup job for a machine with Veeam Plug-In for IBM Db2. All backup sessions for different databases that reside on this machine run within this backup job.
* Veeam Backup & Replication generates names for IBM Db2 backup jobs according to the names of the machine with Veeam Plug-In.

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](db2_protection_job_vbr_statistics.md)
* [Generate a backup job report](db2_protection_job_vbr_reports.md)
* [Disable a backup job](db2_protection_job_vbr_disable.md)
* [Delete a backup job](db2_protection_job_vbr_delete.md)


