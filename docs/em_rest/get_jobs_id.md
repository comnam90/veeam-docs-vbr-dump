---
title: "GET /jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_jobs_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /jobs/{ID}


Returns a resource representation of the job resource having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a resource representation of the job, send the GET HTTP request to the /jobs/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/jobs/{ID} |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /jobs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the job, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| Name | String | Name of the job, for example: DC Replication. |
| JobType | String | Job type. Possible values:   * Backup — backup job * BackupCopy — periodic backup copy job * ImmediateBackupCopy — immediate backup copy job * Replica — replication job |
| Platform | String | Platform for which the job is created. Possible values:   * VMware * Hyperv * vCloud |
| Description | String | Description of the job specified at the time of the job creation. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| NextRun | DateTime | Date and time of the next job run. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z.  Note that this parameter can be used for scheduled jobs only. |
| JobScheduleOptions | ScheduleOptionsInfoType | Options that define the schedule by which the job runs. For details, see [Job Scheduling Options](jobscheduleoptions.md). |
| JobInfo | — | Object that includes one of the following complex objects depending on the job type:   * BackupJobInfo * ReplicaJobInfo * BackupCopyJobInfo * ImmediateBackupCopyJobInfo   For details, see [Job Info](jobinfo.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Job](get_query_job.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the job was configured. |
| /jobs/{ID} | Alternate | Alternate URL of the [/jobs/{ID}](jobs_id.md) resource. |
| /jobs/{ID} | Edit | URL for the [PUT /jobs/{ID}](put_jobs_id_actionedit.md) request. |
| /jobs/{ID}?action=start | Start | URL for the [POST /jobs/{ID}?action=start](post_jobs_id_actionstart.md) request. It's available for backup and replication jobs. |
| /jobs/{ID}?action=stop | Stop | URL for the [POST /jobs/{ID}?action=stop](post_jobs_id_actionstop.md) request. |
| /jobs/{ID}?action=retry | Retry | URL for the [POST /jobs/{ID}?action=retry](post_jobs_id_actionretry.md) request. |
| /jobs/{ID}?action=clone | Clone | URL for the [POST /jobs/{ID}?action=clone](post_jobs_id_actionclone.md) request. |
| /jobs/{ID}?action=toggleScheduleEnabled | ToggleScheduleEnabled | URL for the [POST /jobs/{ID}?action=toggleScheduleEnabled](post_jobs_id_actiontogglescheduleenabled.md) request. |
| /jobs/{ID}/includes | Down | URL of the [/jobs/{ID}/includes](jobs_id_includes.md) resource — a collection of VMs and VM containers processed by the job. |
| /jobs/{ID}/includes | Create | URL for the [POST /jobs/{ID}/includes](post_jobs_id_includes.md) request. |
| /jobs/{ID}/backupSessions | Down | URL of the [/jobs/{ID}/includes](jobs_id_includes.md) resource — a collection of backup job sessions initiated for the job. |
| /jobs/{ID}?action=sync | Sync | URL for the [POST /jobs/{ID}?action=sync](post_jobs_id_actionsync.md) request. It's available for backup copy jobs only. |
| /jobs/{ID}/linkedJobs | Down | It's available for backup copy jobs only. |
| /jobs/{ID}/linkedJobs | Create | It's available for backup copy jobs only. |
| /jobs/{ID}/linkedBackupRepositories | Down | It's available for backup copy jobs only. |
| /jobs/{ID}/linkedBackupRepositories | Create | It's available for backup copy jobs only. |

Example 1. Backup Job

The example below returns an entity resource representation of a backup job.

|  |
| --- |
| Request:  GET https://localhost:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <Job xmlns="http://www.veeam.com/ent/v1.0" Type="Job" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?format=Entity" Name="DB Backup" UID="urn:veeam:Job:5658281f-625e-4627-89dd-d2a0c48be99e">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e" Name="DB Backup" />     <Link Rel="Edit" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e" Name="DB Backup" />     <Link Rel="Clone" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=clone" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=toggleScheduleEnabled" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/backupSessions" />     <Link Rel="Create" Type="ObjectInJob" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=retry" />   </Links>   <JobType>Backup</JobType>   <Platform>HyperV</Platform>   <Description>Backup of MS SQL Server DB</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2025-02-01T17:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>18:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions>   <JobInfo>     <BackupJobInfo>       <Includes>         <ObjectInJob Type="ObjectInJob" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes/0493ea16-2c1f-4d02-b74b-994bd438b89a">           <ObjectInJobId>0493ea16-2c1f-4d02-b74b-994bd438b89a</ObjectInJobId>           <HierarchyObjRef>urn:HyperV:Vm:8e7fef9f-87a8-48b4-bed1-632c3035a1a1.020aa5ab-3523-4946-b658-b8ad5b372439</HierarchyObjRef>           <Name>sqlsrv03</Name>           <DisplayName>sqlsrv03</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>false</IsCopyOnly>               <UsePersistentGuestAgent>false</UsePersistentGuestAgent>             </VssSnapshotOptions>             <WindowsGuestFSIndexingOptions>               <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>               <IncludedIndexingFolders />               <ExcludedIndexingFolders>                 <Path>%windir%</Path>                 <Path>%ProgramFiles%</Path>                 <Path>%ProgramFiles(x86)%</Path>                 <Path>%ProgramW6432%</Path>                 <Path>%TEMP%</Path>               </ExcludedIndexingFolders>             </WindowsGuestFSIndexingOptions>             <LinuxGuestFSIndexingOptions>               <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>               <IncludedIndexingFolders />               <ExcludedIndexingFolders>                 <Path>/cdrom</Path>                 <Path>/dev</Path>                 <Path>/media</Path>                 <Path>/mnt</Path>                 <Path>/proc</Path>                 <Path>/tmp</Path>                 <Path>/lost+found</Path>               </ExcludedIndexingFolders>             </LinuxGuestFSIndexingOptions>             <SqlBackupOptions>               <TransactionLogsProcessing>Backup</TransactionLogsProcessing>               <BackupLogsFrequencyMin>60</BackupLogsFrequencyMin>               <UseDbBackupRetention>false</UseDbBackupRetention>               <RetainDays>5</RetainDays>             </SqlBackupOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>       </Includes>       <GuestProcessingOptions>         <VssSnapshotOptions>           <VssSnapshotMode>RequireSuccess</VssSnapshotMode>           <IsCopyOnly>false</IsCopyOnly>         </VssSnapshotOptions>         <WindowsGuestFSIndexingOptions>           <FileSystemIndexingMode>EveryFolders</FileSystemIndexingMode>           <IncludedIndexingFolders />           <ExcludedIndexingFolders />         </WindowsGuestFSIndexingOptions>         <LinuxGuestFSIndexingOptions>           <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>           <IncludedIndexingFolders />           <ExcludedIndexingFolders />         </LinuxGuestFSIndexingOptions>         <SqlBackupOptions>           <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>           <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>           <UseDbBackupRetention>true</UseDbBackupRetention>           <RetainDays>15</RetainDays>         </SqlBackupOptions>         <WindowsCredentialsId>7255bb17-aa93-44d0-9a24-00b9cd1da6c4</WindowsCredentialsId>         <LinuxCredentialsId />       </GuestProcessingOptions>       <AdvancedStorageOptions>         <PasswordKeyId>3d152e9d-a473-4990-bc2f-27710833ba20</PasswordKeyId>       </AdvancedStorageOptions>       <GfsRetentionPolicy Enabled="true">         <Weekly>           <Enabled>true</Enabled>           <RetentionPeriod>2</RetentionPeriod>           <SelectedDay>Sunday</SelectedDay>         </Weekly>         <Monthly>           <Enabled>true</Enabled>           <RetentionPeriod>3</RetentionPeriod>           <SelectedWeek>First</SelectedWeek>         </Monthly>         <Yearly>           <Enabled>true</Enabled>           <RetentionPeriod>1</RetentionPeriod>           <SelectedMonth>January</SelectedMonth>         </Yearly>       </GfsRetentionPolicy>       <SimpleRetentionPolicy>         <RetainCycles>5</RetainCycles>         <RetainDaysToKeep>7</RetainDaysToKeep>         <RetainLimitType>Cycles</RetainLimitType>       </SimpleRetentionPolicy>     </BackupJobInfo>   </JobInfo> </Job> |

Example 2. Immediate Backup Copy Job

The example below returns an entity resource representation of an immediate backup copy job.

|  |
| --- |
| <Job xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b?format=Entity" Type="Job" Name="Immediate Backup Copy Job" UID="urn:veeam:Job:5adf6525-51d9-48b9-a72d-7f80701c714b" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterpriseem01.tech.local:9398/api/backupServers/3cbab7db-fa0d-4c18-82b6-bc1816f0a128" Name="enterprisevbr01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b" Name="Immediate Backup Copy Job" Type="JobReference" Rel="Alternate" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b?action=clone" Rel="Clone" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b?action=toggleScheduleEnabled" Rel="ToggleScheduleEnabled" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b?action=sync" Rel="Sync" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b/linkedJobs" Type="LinkedJobObjectList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b/linkedBackupRepositories" Type="LinkedBackupRepositoryObjectList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b/linkedJobs" Type="LinkedJobObject" Rel="Create" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/5adf6525-51d9-48b9-a72d-7f80701c714b/linkedBackupRepositories" Type="LinkedBackupRepositoryObject" Rel="Create" />     </Links>     <JobType>ImmediateBackupCopy</JobType>     <Platform>CustomPlatform</Platform>     <Description>Created by .\veeamadmin</Description>     <ScheduleConfigured>true</ScheduleConfigured>     <ScheduleEnabled>true</ScheduleEnabled>     <JobScheduleOptions>         <ImmediateCopyMode>             <OptionsContinuous Enabled="true">                 <Schedule>                     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Tuesday">1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1</Day>                     <Day Name="Wednesday">1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1</Day>                     <Day Name="Thursday">1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1</Day>                     <Day Name="Friday">1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1</Day>                     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 </Schedule>             </OptionsContinuous>         </ImmediateCopyMode>     </JobScheduleOptions>     <JobInfo>         <ImmediateBackupCopyJobInfo>             <LinkedJobIncludes>                 <LinkedJobObject>                     <ObjectInJobId>64d63522-92a0-491c-af3b-e428019fbfd4</ObjectInJobId>                     <LinkedJobUid>urn:veeam:Job:33fecc36-554b-437b-8bf8-3fdcb11866e7</LinkedJobUid>                 </LinkedJobObject>             </LinkedJobIncludes>             <LinkedBackupIncludes />             <LinkedBackupRepositoryIncludes />         </ImmediateBackupCopyJobInfo>     </JobInfo> </Job> |

Example 3. Periodic Backup Copy Job

The example below returns an entity resource representation of a periodic backup copy job created with Veeam Backup & Replication 13.

|  |
| --- |
| <Job xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b?format=Entity" Type="Job" Name="Periodic Backup Copy Job" UID="urn:veeam:Job:0f5afb99-7468-42c4-a45d-28e98bc6122b" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterpriseem01.tech.local:9398/api/backupServers/3cbab7db-fa0d-4c18-82b6-bc1816f0a128" Name="enterprisevbr01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b" Name="Periodic Backup Copy Job" Type="JobReference" Rel="Alternate" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b?action=clone" Rel="Clone" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b?action=toggleScheduleEnabled" Rel="ToggleScheduleEnabled" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b?action=sync" Rel="Sync" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedJobs" Type="LinkedJobObjectList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedBackupRepositories" Type="LinkedBackupRepositoryObjectList" Rel="Down" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedJobs" Type="LinkedJobObject" Rel="Create" />         <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedBackupRepositories" Type="LinkedBackupRepositoryObject" Rel="Create" />     </Links>     <JobType>ImmediateBackupCopy</JobType>     <Platform>CustomPlatform</Platform>     <Description>Created by .\veeamadmin (for repository)</Description>     <ScheduleConfigured>true</ScheduleConfigured>     <ScheduleEnabled>true</ScheduleEnabled>     <JobScheduleOptions>         <ImmediateCopyMode>             <OptionsContinuous Enabled="false">                 <Schedule>                     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 </Schedule>             </OptionsContinuous>         </ImmediateCopyMode>     </JobScheduleOptions>     <JobInfo>         <ImmediateBackupCopyJobInfo>             <LinkedJobIncludes />             <LinkedBackupIncludes />             <LinkedBackupRepositoryIncludes>                 <LinkedBackupRepository>                     <ObjectInJobId>961c9350-dc5a-43d6-8efa-867995e9404e</ObjectInJobId>                     <LinkedBackupRepositoryUid>urn:veeam:Repository:da49abfc-838a-40a1-90a3-40acd2bc7000</LinkedBackupRepositoryUid>                 </LinkedBackupRepository>             </LinkedBackupRepositoryIncludes>         </ImmediateBackupCopyJobInfo>     </JobInfo> </Job> |

Page updated 2026-07-28

