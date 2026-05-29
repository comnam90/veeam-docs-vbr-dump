---
title: "Managing Backup Jobs in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_job_vbr.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Managing Backup Jobs in Veeam Backup & Replication


After Veeam Plug-In for Microsoft SQL Server starts the backup process, Veeam Backup & Replication creates the backup job. You can use this job to view statistics on the backup process and generate backup job reports. You can also disable the backup job.

You cannot start or edit Microsoft SQL Server backup jobs in the Veeam Backup & Replication console. You can manage backup operations on Microsoft SQL Server only.

Consider the following:

* Veeam Backup & Replication creates one backup job for a standalone Microsoft SQL Server, Microsoft SQL Server failover cluster or Always On availability group. All backup sessions for different databases that reside on this server, cluster or availability group run within this backup job.
* Veeam Backup & Replication generates names for Microsoft SQL Server backup jobs according to the following rules:

* For standalone Microsoft SQL Server, Veeam Backup & Replication generates the backup job name based on the names of Microsoft SQL Server and backup repository where Veeam Plug-In creates Microsoft SQL Server backups.
* For Microsoft SQL Server that operates as part of a failover cluster or availability group, Veeam Backup & Replication generates the backup job name based on the name of the cluster or name of the availability group.

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](plugins_mssql_job_vbr_statistics.md)
* [Generate a backup job report](plugins_mssql_job_vbr_reports.md)
* [Disable a backup job](plugins_mssql_job_vbr_disable.md)
* [Delete a backup job](plugins_mssql_job_vbr_delete.md)


