---
title: "Policy Scheduling Options"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/policyscheduleoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The PolicyScheduleOptions element of the CDP policy resource contains the following scheduling options for the CDP policy.

| Element | Type | Description |
| --- | --- | --- |
| RecoveryPointObjectiveSeconds | Int64 | Recovery point objective in seconds. |
| RecoveryPointObjectiveMinutes | Int64 | Recovery point objective in minutes. |
| RPOSchedule | RPOScheduleType | Time intervals that define when the CDP policy is allowed to create a replicated state of the source VMs. For details, see [RPO Schedule Options](#rpo). |
| RPOReporting | RPOReportingType | Defines RPO reporting settings. For details, see [RPO Reporting Options](#reporting). |
| ShortTermRetentionMinutes | Int64 | Time period for which short-term restore points must be stored, in minutes. |
| ShortTermRetentionHours | Int64 | Time period for which short-term restore points must be stored, in hours. |
| LongTermRetentionHours | Int64 | Defines how often new long-term restore points must be created, in hours. |
| LongTermRetentionKeepDays | Int64 | Defines for how long the long-term restore points must be retained, in days. |
| LongTermRetentionSchedule | LongTermRetentionScheduleType | Time intervals that define when the CDP policy must create application-consistent and when crash-consistent long-term restore points. For details, see [Long-Term Retention Schedule Options](#long_term). |

RPO Schedule Options

The RPOSchedule element contains the following RPO schedule options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether RPO schedule options are specified for the CDP policy. |
| TimePeriods | TimePeriodsType | Defines an hourly scheme by which the CDP policy must run. The schedule scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the CDP policy must run, 0 means the CDP policy must not run. |

RPO Reporting Options

The RPOReporting element contains the following RPO reporting options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether RPO reporting options are specified for the job. |
| MarkAsWarning | CDPReplicaRPOReportingWarningOptionsType | Time interval in seconds or minutes before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. For details, see [Warning Settings](#warning). |
| MarkAsFailed | CDPReplicaRPOReportingFailedOptionsType | Time interval in seconds or minutes before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. For details, see [Error Settings](#error). |

Warning Settings

The MarkAsWarning element contains the following warning settings.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether warning notifications are enabled. |
| RPOThresholdSeconds | Int | Time interval in seconds before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. |
| RPOThresholdMinutes | Int | Time interval in minutes before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. |

Error Settings

The MarkAsFailed element contains the following error settings.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether error notifications are enabled. |
| RPOThresholdSeconds | Int | Time interval in seconds before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. |
| RPOThresholdMinutes | Int | Time interval in minutes before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. |

Long-Term Retention Schedule Options

The LongTermRetentionSchedule element contains the following periodic scheduling options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether long-term retention schedule options are specified for the job. |
| Schedule | TimePeriodsType | Defines an hourly scheme when the CDP policy must create application-consistent and when crash-consistent long-term restore points. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the CDP policy must create crash-consistent long-term restore points, 2 means the CDP policy must create application-consistent long-term restore points. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
