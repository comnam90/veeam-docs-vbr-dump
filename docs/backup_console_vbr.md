---
title: "Managing Backup Jobs in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_console_vbr.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Managing Backup Jobs in Veeam Backup & Replication


|  |
| --- |
| Tip |
| If you want to configure or manage an application backup policy for Veeam Plug-In operating in the managed mode, see [Working with Application Policies](application_policies.md). |

After you start a backup process with SAP HANA Backint, Veeam Backup & Replication creates a backup job. You can use this job to view the statistics on the backup process, generate backup job reports or you can also disable the backup job. You cannot launch or edit SAP HANA backup jobs in the Veeam Backup & Replication console. You can manage backup operations only on the SAP HANA side using SAP HANA Studio, SAP HANA Cockpit or HDBSQL.

Consider the following regarding the naming of SAP HANA backup jobs:

* For a standalone SAP HANA server (scale-up), Veeam Backup & Replication generates the backup job name based on names of the SAP HANA server and selected repository.
* For a scale-out SAP HANA cluster: When you run the Veeam Plug-In configuration wizard for the first time in one of the SAP HANA cluster nodes, the wizard asks for the cluster name. The cluster name will be used in the backup job name along with the repository name.

|  |
| --- |
| Note |
| Due to specifics of the SAP HANA backup process, the progress bar of a running SAP HANA backup job is not available. |

You can perform the following operations from the Veeam Backup & Replication console:

* [View backup job statistics](plugins_backup_console_vbr_statistics.md)
* [Generate a backup job report](plugins_backup_console_vbr_reports.md)
* [Disable a backup job](plugins_backup_console_vbr_disable.md)
* [Delete a backup job](plugins_backup_console_vbr_delete.md)


