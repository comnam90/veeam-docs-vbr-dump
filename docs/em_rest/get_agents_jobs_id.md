---
title: "GET /agents/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_jobs_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/jobs/{ID}


Returns a resource representation of the Veeam Agent backup job resource having the specified ID. The Veeam Agent backup job is configured in Veeam Backup & Replication.

Request

To get a resource representation of the Veeam Agent backup job, send the GET HTTP request to the /agents/jobs/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/jobs/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /agents/jobs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the Veeam Agent backup job, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| Name | String | Name of the Veeam Agent backup job, for example: Linux job. |
| JobType | String | Defines Veeam Agent backup job type. Possible value: AgentBackup. |
| Platform | String | Platform for which the job is created. Possible values:   * AgentForLinux * AgentForWindows |
| Description | String | Description of the job. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| JobScheduleOptions | ScheduleOptionsInfoType | Options that define the schedule by which the job runs. For details, see [Job Scheduling Options](jobscheduleoptions.md). |
| JobInfo | — | Complex object that includes a collection of machines processed by the job. For details, see [GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md#response_body). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=AgentBackupJob](get_query_agentbackupjob.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the Veeam Agent backup job was configured. |
| /agents/jobs/{ID} | Alternate | Alternate URL of the [/agents/jobs/{ID}](agents_jobs_id.md) resource. |
| /agents/jobs/{ID}/includes | Down | URL of the [/agents/jobs/{ID}/includes](agents_jobs_id_includes.md) resource — a list of protected computers and protection groups processed by the Veeam Agent backup job. |
| /agents/jobs/{ID}?action=toggleScheduleEnabled | ToggleScheduleEnabled | URL for the [POST /agents/jobs/{ID}?action=toggleScheduleEnabled](post_agents_jobs_id_actiontogglescheduleenabled.md) request. |
| /agents/jobs/{ID}/backupSessions | Down | URL of the [/agents/backupSessions](agents_backupsessions.md) resource — a collection of backup sessions performed for the Veeam Agent backup job. |
| /agents/jobs/{ID}?action=start | Start | URL for the [POST /agents/jobs/{ID}?action=start](post_agents_jobs_id_actionstart.md) request. |
| /agents/jobs/{ID}?action=stop | Stop | URL for the [POST /agents/jobs/{ID}?action=stop](post_agents_jobs_id_actionstop.md) request. |
| /agents/jobs/{ID}?action=retry | Retry | URL for the [POST /agents/jobs/{ID}?action=retry](post_agents_jobs_id_actionretry.md) request. |

Example

The example below returns an entity resource representation of the Veeam Agent backup job having ID a6deb158-b26c-4140-8b26-5a3cc344e8ec.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <AgentBackupJob xmlns="http://www.veeam.com/ent/v1.0" Type="AgentBackupJob" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?format=Entity" Name="Server Backup" UID="urn:veeam:AgentBackupJob:a6deb158-b26c-4140-8b26-5a3cc344e8ec">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec" Name="Server Backup" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/includes" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=toggleScheduleEnabled" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/backupSessions" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=retry" />   </Links>   <JobType>AgentBackup</JobType>   <Platform>AgentForWindows</Platform>   <Description>Backup of physical server</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2025-02-12T15:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>16:00:00.0000000+01:00</Time>         <TimeOffsetUtc>2</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>2</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions>   <JobInfo>     <Includes>       <ObjectInAgentBackupJob Type="ObjectInAgentBackupJob" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/includes/51616f00-6107-48a9-95ba-1cee9ed6a86e">         <ObjectInJobId>51616f00-6107-48a9-95ba-1cee9ed6a86e</ObjectInJobId>         <Name>Windows Servers</Name>         <DisplayName>Windows Servers</DisplayName>         <GuestProcessingOptions>           <VssSnapshotOptions>             <VssSnapshotMode>RequireSuccess</VssSnapshotMode>             <IsCopyOnly>false</IsCopyOnly>           </VssSnapshotOptions>           <WindowsGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>%windir%</Path>               <Path>%ProgramFiles%</Path>               <Path>%ProgramFiles(x86)%</Path>               <Path>%ProgramW6432%</Path>               <Path>%TEMP%</Path>             </ExcludedIndexingFolders>           </WindowsGuestFSIndexingOptions>           <LinuxGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>/cdrom</Path>               <Path>/dev</Path>               <Path>/media</Path>               <Path>/mnt</Path>               <Path>/proc</Path>               <Path>/tmp</Path>               <Path>/lost+found</Path>             </ExcludedIndexingFolders>           </LinuxGuestFSIndexingOptions>           <SqlBackupOptions>             <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>             <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>             <UseDbBackupRetention>true</UseDbBackupRetention>             <RetainDays>15</RetainDays>           </SqlBackupOptions>           <WindowsCredentialsId />           <LinuxCredentialsId />         </GuestProcessingOptions>       </ObjectInAgentBackupJob>     </Includes>     <GuestProcessingOptions>       <VssSnapshotOptions>         <VssSnapshotMode>RequireSuccess</VssSnapshotMode>         <IsCopyOnly>false</IsCopyOnly>       </VssSnapshotOptions>       <WindowsGuestFSIndexingOptions>         <FileSystemIndexingMode>EveryFolders</FileSystemIndexingMode>         <IncludedIndexingFolders />         <ExcludedIndexingFolders />       </WindowsGuestFSIndexingOptions>       <LinuxGuestFSIndexingOptions>         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>         <IncludedIndexingFolders />         <ExcludedIndexingFolders />       </LinuxGuestFSIndexingOptions>       <SqlBackupOptions>         <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>         <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>         <UseDbBackupRetention>true</UseDbBackupRetention>         <RetainDays>15</RetainDays>       </SqlBackupOptions>       <WindowsCredentialsId />       <LinuxCredentialsId />     </GuestProcessingOptions>     <GfsRetentionPolicy Enabled="false">       <Weekly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedDay>Sunday</SelectedDay>       </Weekly>       <Monthly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedWeek>First</SelectedWeek>       </Monthly>       <Yearly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedMonth>January</SelectedMonth>       </Yearly>     </GfsRetentionPolicy>     <SimpleRetentionPolicy>       <RetainCycles>5</RetainCycles>       <RetainDaysToKeep>7</RetainDaysToKeep>       <RetainLimitType>Cycles</RetainLimitType>     </SimpleRetentionPolicy>   </JobInfo> </AgentBackupJob> |

Page updated 2026-07-28

