---
title: "Managing Backup Jobs in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vbr.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Managing Backup Jobs in Veeam Backup & Replication


|  |
| --- |
| Tip |
| If you want to configure or manage an application backup policy for Veeam Plug-In operating in the managed mode, see [Working with Application Policies](application_policies.md). |

After you start a backup process with the BRBACKUP tool, Veeam Backup & Replication creates a backup job object. You can use this job to view the statistics on the backup process, generate backup job reports or you can also disable the backup job.

You cannot launch or edit SAP on Oracle backup job objects in the Veeam Backup & Replication console. You can manage backup operations only on the SAP on Oracle side using BR\*Tools.

Consider that Veeam Backup & Replication generates the backup job name based on names of the SAP on Oracle server and selected repository.

|  |
| --- |
| Note |
| Due to specifics of the SAP on Oracle backup process, the progress bar of a running SAP on Oracle backup job is not available. |

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](plugins_backup_job_vbr_statistics.md)
* [Generate a backup job report](plugins_backup_job_vbr_reports.md)
* [Disable a backup job](plugins_backup_job_vbr_disable.md)
* [Delete a backup job](plugins_backup_job_vbr_delete.md)


