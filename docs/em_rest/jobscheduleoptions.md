---
title: "Job Scheduling Options"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobscheduleoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The JobScheduleOptions element of the job resource contains the following job scheduling options.

| Element | Type | Description |
| --- | --- | --- |
| RetryOptions | JobScheduleRetryOptionsType | Retry options set for the job. For details, see [Retry Options](#retry). |
| WaitForBackupCompletion | Boolean | This parameter is set for SureBackup and backup copy jobs. Defines whether the job must wait for the backup or replication job to complete. |
| BackupCompetitionWaitingPeriodMin | Int64 | Time period in minutes for which the job must wait for the backup job to complete. |
| OptionsDaily | JobScheduleDailyOptionsType | Daily backup options set for the job. For details, see [Daily Backup Scheduling Options](#daily). |
| OptionsMonthly | JobScheduleMonthlyOptionsType | Monthly backup options set for the job. For details, see [Monthly Backup Scheduling Options](#month). |
| OptionsPeriodically | JobSchedulePeriodicallyOptionsType | Periodic backup options set for the job. For details, see [Periodic Backup Scheduling Options](#periodic). |
| OptionsContinuous | JobScheduleContinuousOptionsType | Continuous backup options set for the job. For details, see [Continuous Backup Scheduling Options](#continuous). |
| OptionsBackupWindow | JobScheduleBackupWindowOptionsType | Backup window options set for the job. For details, see [Backup Window Options](#window). |
| OptionsDaisyChaining | JobScheduleDaisyChainingOptionsType | Defines whether backup job chaining is enabled for the job. For details, see [Job Chaining Options](#chain). |

Retry Options

The RetryOptions element of the job resource contains the following retry options.

| Element | Type | Description |
| --- | --- | --- |
| RetryTimes | Int64 | Number of retries set for the job. |
| RetryTimeout | Int64 | Time interval between job retries |
| RetrySpecified | Boolean | Defines whether retry options are set for the job. |

Daily Backup Scheduling Options

The OptionsDaily element of the job resource contains the following daily backup options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether daily scheduling options are specified for the job. |
| Kind | String | Kind of daily scheduling scheme. Possible values:   * Everyday * WeekDays * SelectedDays |
| Days | DaysOfWeekEnumeration | Days on which the job must be launched. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday |
| Time | Time | Daily time interval within which the job session should be completed. |
| TimeOffsetUtc | TimeSpan | UTC offset. |

Monthly Backup Scheduling Options

The OptionsMonthly element of the job resource contains the following monthly backup options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether monthly scheduling options are specified for the job. |
| Time | Time | Daily time interval within which the job session should be completed. |
| TimeOffsetUtc | TimeSpan | UTC offset. |
| DayOfWeek | String | Days on which the job must be launched. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday |
| Months | JobScheduleMonthEnumeration | Months on which the job must be launched. Possible values:   * January * February * March * April * May * June * July * August * September * October * November * December |
| DayNumberInMonth | String | Day in month on which the backup job must be launched. |

Periodic Backup Scheduling Options

The OptionsPeriodically element of the job resource contains the following periodic backup scheduling options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether periodic scheduling options are specified for the job. |
| Kind | String | Defines the time unit for periodic job scheduling. Possible values:   * Hours * Minutes |
| FullPeriod | Int64 | Defines periodic cycles (in hours or minutes depending on the value of the Kind element) in which the job must be launched.   * The hours value must be between 1 and 24 * The minutes value must be between 1 and 60 |
| Schedule | TimePeriodsType | Defines an hourly scheme by which the job must be launched. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. |

Continuous Backup Scheduling Options

The OptionsContinuous element of the job resource contains the following continuous backup scheduling options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether continuous scheduling options are specified for the job. |
| Schedule | TimePeriodsType | Defines an hourly scheme by which the job can continuously perform. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. |

Backup Window Options

The OptionsBackupWindow element of the job resource contains the following backup window options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether backup window options are specified for the job. |
| TimePeriods | TimePeriodsType | Defines an hourly scheme for the backup window. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. |

Job Chaining Options

The OptionsDaisyChaining element of the job resource contains the following job chaining options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether job chaining is enabled. |
| PreviousJobUid | UidType | UID of the previous job in the chain, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |

Retention Policy Options

You can define the following retention policy options for the job:

* [Short-term retention policy](#simpleretention)
* [Long-term (GFS) retention policy](#gfsretention)

Short-Term Retention Policy Options

The SimpleRetentionPolicy element of the job resource contains the following job scheduling options.

| Element | Type | Description |
| --- | --- | --- |
| RetainCycles | Int64 | Number restore points to keep. |
| RetainDaysToKeep | Int64 | Number of days for which to keep restore points. |
| RetainLimitType | String | Defines whether to keep a specific number of restore points or restore points created during a specific number of days: Possible values:   * Cycles —  keep the last <N> restore points, where <N> is the specified number of restore points. * Days — keep restore points created during the last <N> days, where <N> is the specified number of days. |

GFS Retention Policy Options

The GfsRetentionPolicy element of the job resource contains the following GFS retention policy options.

| Element | Type | Description |
| --- | --- | --- |
| Weekly | WeeklyOptionsInfoType | Weekly GFS retention policy options set for the job. For details, see [Weekly GFS Retention Policy Options](#weeklyretention). |
| Monthly | MonthlyOptionsInfoType | Monthly GFS retention policy options set for the job. For details, see [Monthly GFS Retention Policy Options](#monthlyretention). |
| Yearly | YearlyOptionsInfoType | Yearly GFS retention policy options set for the job. For details, see [Yearly GFS Retention Policy Options](#yearlyretention). |

Weekly GFS Retention Policy Options

The Weekly element of the job resource contains the following weekly GFS retention policy options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether weekly GFS retention policy settings are enabled. |
| RetentionPeriod | Int64 | Number of weeks to keep full backups for archival purposes. |
| SelectedDay | String | Day of the week when the full backup that will be kept for archival purposes is created. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday |

Monthly GFS Retention Policy Options

The Monthly element of the job resource contains the following monthly GFS retention policy options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether monthly GFS retention policy settings are enabled. |
| Retention period | Int64 | Number of months to keep full backups for archival purposes. |
| SelectedWeek | String | Week of the month when the full backup that will be kept for archival purposes is created. Possible values:   * First * Last |

Yearly GFS Retention Policy Options

The Yearly element of the job resource contains the following yearly GFS retention policy options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether yearly GFS retention policy settings are enabled. |
| Retention period | Int64 | Number of years to keep full backups for archival purposes. |
| SelectedMonth | String | Month when the full backup that will be kept for archival purposes is created. Possible values:   * January * February * March * April * May * June * July * August * September * October * November * December |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
