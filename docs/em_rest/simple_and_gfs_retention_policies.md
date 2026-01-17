---
title: "Simple and GFS Retention Policies"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/simple_and_gfs_retention_policies.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---


In this article

You can define the following retention policy options for the job:

* [Short-term retention policy](#simpleretention)
* [Long-term (GFS) retention policy](#gfsretention)

Short-Term Retention Policy Options

Short-term retention policy options must be defined in the SimpleRetentionPolicy element of the BackupJobInfo element.

Short-term retention policy options are provided in the following format:

XML Representation

|  |
| --- |
| <SimpleRetentionPolicy> |

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

Long-term (GFS) retention policy options must be defined in the GFSRetentionPolicy element of the BackupJobInfo element.

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

Page updated 11/27/2025

Page content applies to build 13.0.1.1071
