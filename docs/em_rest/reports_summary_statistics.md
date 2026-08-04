---
title: "/reports/summary/job\_statistics"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_statistics.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /reports/summary/job\_statistics


Represents a report informing about performed jobs, their status, duration and other job-related information.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary/job\_statistics |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary/job\_statistics resource:

[GET /reports/summary/statistics](get_reports_summary_statistics.md)

Resource Representation

The /reports/summary/job\_statistics resource has a resource representation of the following type:

|  |
| --- |
| <JobStatisticsReportFrame xmlns="http://www.veeam.com/ent/v1.0">   <RunningJobs>0</RunningJobs>   <ScheduledJobs>2</ScheduledJobs>   <ScheduledBackupJobs>2</ScheduledBackupJobs>   <ScheduledReplicaJobs>0</ScheduledReplicaJobs>   <TotalJobRuns>12</TotalJobRuns>   <SuccessfulJobRuns>7</SuccessfulJobRuns>   <WarningsJobRuns>0</WarningsJobRuns>   <FailedJobRuns>5</FailedJobRuns>   <MaxJobDuration>2160</MaxJobDuration>   <MaxBackupJobDuration>2160</MaxBackupJobDuration>   <MaxReplicaJobDuration>960</MaxReplicaJobDuration>   <MaxDurationBackupJobName>Backup\_2025-10-18T044119</MaxDurationBackupJobName>   <MaxDurationReplicaJobName>Fileserver02 Replication</MaxDurationReplicaJobName>   <BackupJobStatusReportLink>Workspace/ViewReport.aspx?definition=7962844d-db6c-4d29-8b6e-4e0f7db0785f&amp;ShowParams=1</BackupJobStatusReportLink> </JobStatisticsReportFrame> |

Page updated 2026-07-29

