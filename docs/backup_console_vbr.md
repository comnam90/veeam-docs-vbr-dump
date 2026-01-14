---
title: "Backup Job in Veeam Backup & Replication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_console_vbr.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Backup Job in Veeam Backup & Replication

In this article

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

To view details of a backup job process, do the following:

1. Open the Veeam Backup & Replication console.
2. In the Home view, expand the Jobs node and click Application Plug-Ins.
3. In the list of jobs, select the SAP HANA backup job to see details of the current backup process or the last backup job session.

[![View Details of Backup Job Process](images/vpsh_job.webp)](images/vpsh_job.webp "View Details of Backup Job Process")

Generating Backup Job Reports

Veeam Backup & Replication can generate reports with details about an SAP HANA backup job session performance. The session report contains the following session statistics: session duration details, details of the session performance, amount of read, processed and transferred data, backup size, compression ratio, list of warnings and errors (if any).

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the necessary job and click Report on the ribbon. You can also right-click the job and select Report.

[![View Report of Backup Job Process](images/vpsh_job_report.webp)](images/vpsh_job_report.webp "View Report of Backup Job Process")

Disabling Backup Job

You can disable SAP HANA backup jobs in the Veeam Backup & Replication console. If you disable the job, you will not be able to run SAP Backint backup commands on the SAP HANA server.

To disable a backup job:

1. Open the Home view.

1. In the inventory pane, select Jobs.

1. In the working area, select the necessary job and click Disable on the ribbon. You can also right-click the job and select Disable.

[![Disable Backup Job](images/vpsh_job_disable.webp)](images/vpsh_job_disable.webp "Disable Backup Job")

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
