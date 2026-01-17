---
title: "PUT /jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_jobs_id_actionedit.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# PUT /jobs/{ID}


Edits a job having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To edit a job, send the PUT HTTP request to the /jobs/{ID}?action=edit URL.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/jobs/{ID}?action=edit |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the edited job. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Note |
| In the request body, you can send all resource properties or only those properties that you want to edit. |

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the elements you want to edit. You can define the following general parameters for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Description | String | Description provided for the job. | Yes | 0/1 |
| ScheduleConfigured | Boolean | Defines whether scheduling options are configured for the job. | Yes | 0/1 |
| ScheduleEnabled | Boolean | Defines whether scheduling settings are enabled for the job. If you set this option to True, you need to [define the schedule](#schedule) by which the job should run in the JobScheduleOptions section of the request. | Yes | 0/1 |
| GfsRetentionPolicy | Boolean | Defines whether long-term (GFS) retention policy settings are enabled for the job. If you set this option to True, you need to [specify GFS retention settings](#gfsretention) for the job in the GFSRetentionPolicy section of the request. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Description": "Backup of SQL database server",   "ScheduleConfigured": true,   "ScheduleEnabled": true,   "Name": "DB Backup",   "UID": "urn:veeam:Job:6c86549b-154f-4566-a76e-52bd64a33aea",   "Href": "https://localhost:9398/api/jobs/6c86549b-154f-4566-a76e-52bd64a33aea?format\u003dEntity"   "Type": "Job" } |

Job Scheduling Options

|  |
| --- |
| Note |
| * Scheduling options for jobs of the Backup, BackupCopy and Replica type must be defined in the Standart element of the JobScheduleOptions section in the request body (see [Example](put_jobs_id_actionedit.md#example)). * Scheduling options for jobs of the ImmediateBackupCopy type must be defined in the ImmediateCopyMode element of the JobScheduleOptions section in the request body. For jobs of this type, only [continuous scheduling options](#continuous) are available. |

You can define the following scheduling options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RetryOptions | JobScheduleRetryOptionsType | Retry options set for the job. For details, see [Retry Options](put_jobs_id_actionedit.md#retry). | Yes | — |
| WaitForBackupCompletion | Boolean | This parameter is set for SureBackup and backup copy jobs. Defines whether the job must wait for the backup or replication job to complete. | Yes | 0/1 |
| BackupCompetitionWaitingPeriodMin | Int64 | Time period in minutes for which the job must wait for the backup job to complete. | Yes | 0/1 |
| OptionsDaily | JobScheduleDailyOptions Type | Daily backup options set for the job. For details, see [Daily Backup Scheduling Options](put_jobs_id_actionedit.md#daily). | Yes | 0/1 |
| OptionsMonthly | JobScheduleMonthly OptionsType | Monthly backup options set for the job. For details, see [Monthly Backup Scheduling Options](put_jobs_id_actionedit.md#month). | Yes | 0/1 |
| OptionsPeriodically | JobSchedulePeriodically OptionsType | Periodic backup options set for the job. For details, see [Periodic Backup Scheduling Options](put_jobs_id_actionedit.md#periodic). | Yes | 0/1 |
| OptionsContinuous | JobScheduleContinuousOptionsType | Continuous backup options set for the job. For details, see [Continuous Backup Scheduling Options](#continuous). | Yes | 0/1 |
| OptionsBackupWindow | JobScheduleBackupWindow OptionsType | Backup window options set for the job. For details, see [Backup Window Options](put_jobs_id_actionedit.md#window). | Yes | 0/1 |
| OptionsDaisyChaining | JobScheduleDaisyChaining OptionsType | Defines whether backup job chaining is enabled for the job. For details, see [Job Chaining Options](put_jobs_id_actionedit.md#chain). | Yes | 0/1 |

Retry Options

Retry options are provided in the following format:

XML Representation

|  |
| --- |
| <RetryOptions>   <RetryTimes>3</RetryTimes>   <RetryTimeout>10</RetryTimeout>   <RetrySpecified>true</RetrySpecified> </RetryOptions> |

JSON Representation

|  |
| --- |
| "RetryOptions": {   "RetryTimes": "3",   "RetryTimeout": "10",   "RetrySpecified": "true" } |

You can define the following retry options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RetryTimes | Int64 | Number of retries set for the job. | Yes | 0/1 |
| RetryTimeout | Int64 | Time interval between job retries | Yes | 0/1 |
| RetrySpecified | Boolean | Defines whether retry options are set for the job. | Yes | 0/1 |

Daily Backup Scheduling Options

Daily scheduling options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsDaily Enabled="true">   <Kind>Everyday</Kind>   <Days>Sunday</Days>   <Days>Monday</Days>   <Days>Tuesday</Days>   <Days>Wednesday</Days>   <Days>Thursday</Days>   <Days>Friday</Days>   <Days>Saturday</Days>   <Time>22:00:00.0000000-07:00</Time>      <TimeOffsetUtc>2</TimeOffsetUtc> </OptionsDaily> |

JSON Representation

|  |
| --- |
| "OptionsDaily": {   "Enabled": "true",   "Kind": "Everyday",   "Days": [     "Sunday",     "Monday",     "Tuesday",     "Wednesday",     "Thursday",     "Friday",     "Saturday"   ],   "Time": "22:00:00.0000000-07:00",   "TimeOffsetUtc": "2" } |

You can define the following daily scheduling options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether daily scheduling options are specified for the job. | Yes | — |
| Kind | String | Kind of daily scheduling scheme. Possible values:   * Everyday * WeekDays * SelectedDays | Yes | 0/1 |
| Days | DaysOfWeekEnumeration | Days on which the job must be launched. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | Yes | 0/unbounded |
| Time | Time | Daily time interval within which the job session should be completed. | Yes | 0/1 |
| TimeOffsetUtc | TimeSpan | UTC offset. | Yes | 0/1 |

Monthly Backup Scheduling Options

Monthly scheduling options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsMonthly Enabled="false">   <Time>22:00:00.0000000-07:00</Time>      <TimeOffsetUtc>2</TimeOffsetUtc>   <DayNumberInMonth>Fourth</DayNumberInMonth>   <DayOfWeek>Saturday</DayOfWeek>   <Months>January</Months>   <Months>February</Months>   <Months>March</Months>   <Months>April</Months>   <Months>May</Months>   <Months>June</Months>   <Months>July</Months>   <Months>August</Months>   <Months>September</Months>   <Months>October</Months>   <Months>November</Months>   <Months>December</Months> </OptionsMonthly> |

JSON Representation

|  |
| --- |
| "OptionsMonthly": {   "Enabled": "false",   "Time": "22:00:00.0000000-07:00",   "TimeOffsetUtc": "2",   "DayNumberInMonth": "Fourth",   "DayOfWeek": "Saturday",   "Months": [     "January",     "February",     "March",     "April",     "May",     "June",     "July",     "August",     "September",     "October",     "November",     "December"   ] } |

You can define the following monthly scheduling options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether monthly scheduling options are specified for the job. | Yes | — |
| Time | Time | Daily time interval within which the job session should be completed. | Yes | 0/1 |
| TimeOffsetUtc | TimeSpan | UTC offset. | Yes | 0/1 |
| DayNumberInMonth | String | Day in month on which the backup job must be launched. | Yes | 0/1 |
| DayOfWeek | String | Days on which the job must be launched. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | Yes | 0/unbounded |
| Months | JobScheduleMonthEnumeration | Months on which the job must be launched. Possible values:   * January * February * March * April * May * June * July * August * September * October * November * December | Yes | 0/unbounded |

Periodic Backup Scheduling Options

Periodic scheduling options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsPeriodically Enabled="false">   <Kind>Hours</Kind>   <FullPeriod>1</FullPeriod>   <Schedule>     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>   </Schedule> </OptionsPeriodically> |

JSON Representation

|  |
| --- |
| "OptionsPeriodically": {   "Enabled": "false",   "Kind": "Hours",   "FullPeriod": "1",   "Schedule": {     "Days": [       {         "Name": "Sunday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Monday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Tuesday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Wednesday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Thursday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Friday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Saturday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       }     ]   } } |

You can define the following periodic scheduling options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether periodic scheduling options are specified for the job. | Yes | — |
| Kind | String | Defines the time unit for periodic job scheduling. Possible values:   * Hours * Minutes | Yes | 0/1 |
| FullPeriod | Int64 | Defines periodic cycles (in hours or minutes depending on the value of the Kind option) in which the job must be launched.   * The hours value must be between 1 and 24 * The minutes value must be between 1 and 60 | Yes | 0/1 |
| Schedule | TimePeriods Type | Defines an hourly scheme by which the job must be launched. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. | Yes | 0/unbounded |

Continuous Backup Scheduling Options

Continuous scheduling options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsContinuous Enabled="false">   <Schedule>     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>   </Schedule> </OptionsContinuous> |

JSON Representation

|  |
| --- |
| "OptionsContinious": {   "Enabled": "false",   "Schedule": {     "Days": [       {         "Name": "Sunday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Monday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Tuesday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Wednesday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Thursday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Friday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Saturday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       }     ]   } } |

You can define the following continuous scheduling options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether continuous scheduling options are specified for the job. | Yes | — |
| Schedule | TimePeriods Type | Defines an hourly scheme by which the job can continuously perform. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. | Yes | 0/unbounded |

Backup Window Options

Backup window options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsBackupWindow Enabled="false">   <TimePeriods>     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>   </TimePeriods> </OptionsBackupWindow> |

JSON Representation

|  |
| --- |
| "OptionsBackupWindow": {   "Enabled": "false",   "TimePeriods": {     "Days": [       {        "Name": "Sunday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Monday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {        "Name": "Tuesday",        "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Wednesday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Thursday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Friday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Saturday",         "Value": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       }     ]   } } |

You can define the following backup window options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether backup window options are specified for the job. | Yes | — |
| TimePeriods | TimePeriods Type | Defines an hourly scheme for the backup window. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the job must be started, 0 means the job must not be started. | Yes | 0/unbounded |

Job Chaining Options

Job chaining options are provided in the following format:

XML Representation

|  |
| --- |
| <OptionsDaisyChaining Enabled="true">   <PreviousJobUid></PreviousJobUid> </OptionsDaisyChaining> |

JSON Representation

|  |
| --- |
| "OptionsDaisyChaining": {   "Enabled": "true",   "PreviousJobUid": "" } |

You can define the following job chaining options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether job chaining is enabled. | Yes | — |
| PreviousJobUid | UidType | UID of the previous job in the chain, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. | Yes | 1/1 |

Retention Policy Options

|  |
| --- |
| Note |
| Retention policy options must be defined in the BackupJobInfo section in the request body. |

You can define the following retention policy options for the job:

* [Short-term retention policy](#simpleretention)
* [Long-term (GFS) retention policy](#gfsretention)

Short-Term Retention Policy Options

|  |
| --- |
| Note |
| Short-term retention policy options must be defined in the SimpleRetentionPolicy element of the BackupJobInfo section in the request body. |

Short-term retention policy options are provided in the following format:

XML Representation

|  |
| --- |
| <SimpleRetentionPolicy>   <RetainCycles>5</RetainCycles>   <RetainDaysToKeep>7</RetainDaysToKeep>   <RetainLimitType>Cycles</RetainLimitType> </SimpleRetentionPolicy> |

JSON Representation

|  |
| --- |
| "SimpleRetentionPolicy": {   "RetainCycles": "5",   "RetainDaysToKeep": "7",   "RetainLimitType": "Cycles" } |

You can define the following short-term retention policy options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RetainCycles | Int64 | Number restore points to keep. | Yes | 0/1 |
| RetainDaysToKeep | Int64 | Number of days for which to keep restore points. | Yes | 0/1 |
| RetainLimitType | String | Defines whether to keep a specific number of restore points or restore points created during a specific number of days: Possible values:   * Cycles —  keep the last <N> restore points, where <N> is the specified number of restore points. * Days — keep restore points created during the last <N> days, where <N> is the specified number of days. | Yes | 0/1 |

GFS Retention Policy Options

|  |
| --- |
| Note |
| Long-term (GFS) retention policy options must be defined in the GFSRetentionPolicy element of the BackupJobInfo section in the request body. |

GFS retention policy options are provided in the following format:

XML Representation

|  |
| --- |
| <GfsRetentionPolicy Enabled="true">    <Weekly>     <Enabled>true</Enabled>     <RetentionPeriod>1</RetentionPeriod>     <SelectedDay>Sunday</SelectedDay>   </Weekly>   <Monthly>     <Enabled>true</Enabled>     <RetentionPeriod>1</RetentionPeriod>     <SelectedWeek>First</SelectedWeek>   </Monthly>   <Yearly>     <Enabled>true</Enabled>     <RetentionPeriod>1</RetentionPeriod>     <SelectedMonth>January</SelectedMonth>   </Yearly> </GfsRetentionPolicy> |

JSON Representation

|  |
| --- |
| "GfsRetentionPolicy": {   "Enabled": "true",   "Weekly": {     "Enabled": "true",     "RetentionPeriod": "1",     "SelectedDay": "Sunday"   },   "Monthly": {     "Enabled": "true",     "RetentionPeriod": "1",     "SelectedWeek": "First"   },   "Yearly": {     "Enabled": "true",     "RetentionPeriod": "1",     "SelectedMonth": "January"   } } |

You can define the following GFS retention policy options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Weekly | WeeklyOptionsInfoType | Weekly GFS retention policy options set for the job. For details, see [Weekly GFS Retention Policy Options](#weeklyretention). | Yes | 0/1 |
| Monthly | MonthlyOptionsInfoType | Monthly GFS retention policy options set for the job. For details, see [Monthly GFS Retention Policy Options](#monthlyretention). | Yes | 0/1 |
| Yearly | YearlyOptionsInfoType | Yearly GFS retention policy options set for the job. For details, see [Yearly GFS Retention Policy Options](#yearlyretention). | Yes | 0/1 |

Weekly GFS Retention Policy Options

Weekly GFS retention policy options are provided in the following format:

XML Representation

|  |
| --- |
| <Weekly>    <Enabled>true</Enabled>    <RetentionPeriod>1</RetentionPeriod>    <SelectedDay>Sunday</SelectedDay> </Weekly> |

JSON Representation

|  |
| --- |
| "Weekly": {   "Enabled": "true",   "RetentionPeriod": "1",   "SelectedDay": "Sunday" } |

You can define the following weekly GFS retention policy options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether weekly GFS retention policy settings are enabled. | Yes | 0/1 |
| RetentionPeriod | Int64 | Number of weeks to keep full backups for archival purposes. | Yes | 0/1 |
| SelectedDay | String | Day of the week when the full backup that will be kept for archival purposes is created. Possible values:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | Yes | 0/1 |

Monthly GFS Retention Policy Options

Monthly GFS retention policy options are provided in the following format:

XML Representation

|  |
| --- |
| <Monthly>    <Enabled>true</Enabled>    <RetentionPeriod>1</RetentionPeriod>    <SelectedWeek>First</SelectedWeek>  </Monthly> |

JSON Representation

|  |
| --- |
| "Monthly": {   "Enabled": "true",   "RetentionPeriod": "1",   "SelectedWeek": "First" } |

You can define the following monthly GFS retention policy options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether monthly GFS retention policy settings are enabled. | Yes | 0/1 |
| RetentionPeriod | Int64 | Number of months to keep full backups for archival purposes. | Yes | 0/1 |
| SelectedWeek | String | Week of the month when the full backup that will be kept for archival purposes is created. Possible values:   * First * Last | Yes | 0/1 |

Yearly GFS Retention Policy Options

Yearly GFS retention policy options are provided in the following format:

|  |
| --- |
| <Yearly>    <Enabled>true</Enabled>    <RetentionPeriod>1</RetentionPeriod>    <SelectedMonth>January</SelectedMonth>  </Yearly> |

JSON Representation

|  |
| --- |
| "Yearly": {   "Enabled": "true",   "RetentionPeriod": "1",   "SelectedMonth": "January" } |

You can define the following yearly GFS retention policy options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether yearly GFS retention policy settings are enabled. | Yes | 0/1 |
| RetentionPeriod | Int64 | Number of years to keep full backups for archival purposes. | Yes | 0/1 |
| SelectedMonth | String | Month when the full backup that will be kept for archival purposes is created. Possible values:   * January * February * March * April * May * June * July * August * September * October * November * December | Yes | 0/1 |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

Example

The example below changes the number of retries to 5 for the job having ID 78c3919c-54d7-43fe-b047-485d3566f11f.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/jobs/78c3919c-54d7-43fe-b047-485d3566f11f?action=edit    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <Job Type="Job" Href="https://localhost:9398/api/jobs/6c86549b-154f-4566-a76e-52bd64a33aea?format=Entity" Name="SQL Backup HV" UID="urn:veeam:Job:d1b85018-2769-45be-89bc-03f66b60e6cb" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <JobScheduleOptions>     <Standart>       <RetryOptions>       <RetryTimes>5</RetryTimes>       </RetryOptions>     </Standart>   </JobScheduleOptions> </Job>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditJob</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


