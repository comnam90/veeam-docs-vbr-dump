---
title: "Application Backup Policies"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_policy.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Application Backup Policies

In this article

To back up databases on your computers with Veeam Plug-Ins, you must configure an application backup policy. An application backup policy is a task that defines what data to back up, how, where and when to back up data.

After you configure the application backup policy on the Veeam Backup & Replication server side, Veeam Plug-Ins create transport jobs on your computers. Using these transport jobs, Veeam Backup & Replication orchestrates the backup operations. Transport jobs collect backed-up data and send it from your computers to the backup repository. Each transport job creates an independent backup. For example, if the application backup policy orchestrates 3 transport jobs, a backup repository will store 3 backup files, one file per each transport job.

Backing Up One Computer with Multiple Policies

You can add a database only to one application backup policy. But, you can still configure several application backup policies to back up different databases on the same computer. For example, if you want to back up a staging database and a production database according to different schedules, you must create two application backup policies. In this case, each of these policies will orchestrate its transport job that will produce a backup and send it to a backup repository.

How Application Backup Policy Works

After you configure an application backup policy, this backup policy functions in the following way:

1. The backup policy is waiting for the next backup run.

For Veeam Plug-In for Microsoft SQL Server, the backup policy is stopped till the next backup run. For other managed Veeam Plug-In, the backup policy is running continuously. When there are no active backup activities, the backup policy is set to an idle state. This state allows the backup policy to catch warnings and display them in the backup policy statistics.

1. Before starting the next backup run, Veeam Backup & Replication finishes the active session. The backup policy sends a report to Veeam Backup & Replication. The finished session becomes available in the History view of the Veeam backup console. To learn more, see [Viewing Backup Policy Report](report_backup_policy_report.md) and [Viewing Backup Policy Statistics](report_backup_policy_stats.md).
2. If database log processing is enabled, the backup policy restarts the database log backup run. Database log backup is a separate task that runs in parallel with the database backup.

|  |
| --- |
| Note |
| For Veeam Plug-In for Oracle RMAN, you cannot disable database log processing. If there is an existing full backup of the database, the backup policy always restarts the database log backup run. |

1. The backup policy creates a list of backup tasks, detects and configure Veeam Plug-Ins. Veeam Plug-Ins run the backup operations on computers.
2. Transport jobs on computers send backed-up data from computers to the backup repository.

An application backup policy may consist of several activities. For example, database backup according to the policy schedule, database logs backup according to a separate schedule, and manual database backup. In this case, Veeam Plug-In will store the backed-up data for all activities in the same backup.

1. The backup policy sends a report to Veeam Backup & Replication about backed-up and transported data.

After the backup run is completed, the backup policy returns to the idle state and waits for the next backup run.

Related Tasks

[Working with Application Policies](application_policies.md)

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
