---
title: "Job Priorities"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/job_priorities.html"
last_updated: "9/30/2025"
product_version: "13.0.1.1071"
---

# Job Priorities

In this article

Resources in the backup infrastructure are limited. To make sure that the most crucial jobs are the first to get free resources to provide the reliable data protection, Veeam Backup & Replication uses the system of priorities to allocate resources to different jobs.

The resource scheduler within Veeam Backup & Replication uses several stages to prioritize jobs and provide free resources to them:

1. Type — at the first stage, the resource scheduler identifies the priority of the jobs awaiting free resources based on their type:

1. Backup restore jobs — these jobs have the highest priority (800) and are the first to get free system resources.
2. Continuous data protection jobs — these jobs have priority (700).
3. SnapshotDeleter jobs — these jobs have priority (600).
4. Quick backup jobs — these jobs have priority (500).
5. High priority jobs — jobs with the enabled High priority option have priority (400). You can enable the High priority option for the following jobs: backup jobs, replication jobs, agent jobs managed by backup server, file backup jobs.

   |  |
   | --- |
   | Tip |
   | In the list of jobs in the Veeam Backup & Replication console, jobs with the High priority option enabled are marked with double green arrows (![Job Priorities](images/high_priority_job.webp)). |
6. Regular backup and replication jobs — these jobs have priority (300).
7. Backup copy jobs — these jobs have priority (200). Immediate backup copy jobs have priority (400) when the related source backup job is a high priority job.
8. Archive jobs — these jobs have the lowest priority (100) and are the last to get free system resources. These are the jobs that move backups to capacity and archive tiers.

1. Priority — at the second stage, the resource scheduler identifies the priority of the jobs within each type group from the first stage based on their startup type:

1. Scheduled VSS proxy jobs — the jobs with the configured job schedule and using a VSS proxy have the highest priority (40) within the group and are the first to get free system resources.
2. Scheduled jobs — the jobs with the configured job schedule have priority (30) within the group.
3. Manually started VSS proxy jobs — the manually started jobs using a VSS proxy have priority (20) within the group.
4. Manually started jobs — the manually started jobs have the lowest priority (10) within the group and are the last to get free system resources.

1. Start time — if the jobs have the same type and priority, resources are first allocated to jobs that were started earlier with an exception of tape jobs.

|  |
| --- |
| Note |
| The resource scheduler does not take into account the start time for tape jobs. The source job may start when the tape job is still running. For more information on the priority settings for tape jobs, see [Schedule for Backup to Tape Job](backup_to_tape_simple_schedule.md). |

You can check the job type and priority of a certain job in service logs. For more information on logs, see [Managing Logs](logging.md).

Page updated 9/30/2025

Page content applies to build 13.0.1.1071
