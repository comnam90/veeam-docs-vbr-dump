---
title: "Managing Backup Jobs in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_job_vbr.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Managing Backup Jobs in Veeam Backup & Replication


|  |
| --- |
| Tip |
| If you want to configure or manage an application backup policy for Veeam Plug-In operating in the managed mode, see [Working with Application Policies](application_policies.md). |

After you start a backup process in Oracle RMAN, Veeam Backup & Replication creates a backup job. You can use this job to view the statistics on the backup process, generate backup job reports or you can also disable the backup job.

You cannot start or edit Oracle RMAN backup jobs in the Veeam Backup & Replication console. You can manage backup operations only on the Oracle side using RMAN.

Consider the following regarding the naming of Oracle RMAN backup jobs:

* For a standalone Oracle RMAN server, Veeam Backup & Replication generates the backup job name based on names of the Oracle RMAN server and selected repository.
* For Oracle RAC, Veeam Backup & Replication generates the backup job name based on single client access name (SCAN) of the cluster.

|  |
| --- |
| Note |
| The progress bar of a running Oracle database backup job is available only for backups of standalone Oracle databases. It is not available for Oracle RAC backups. |

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](plugins_rman_job_vbr_statistics.md)
* [Generate a backup job report](plugins_rman_job_vbr_reports.md)
* [Disable a backup job](plugins_rman_job_vbr_disable.md)
* [Delete a backup job](plugins_rman_job_vbr_delete.md)


