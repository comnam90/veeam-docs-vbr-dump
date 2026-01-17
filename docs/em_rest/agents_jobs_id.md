---
title: "/agents/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_jobs_id.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---

# /agents/jobs/{ID}


Represents a Veeam Agent backup job having the specified ID. The Veeam Agent backup job is configured in Veeam Backup & Replication.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/jobs/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/jobs/{ID}?format=Entity |

Related Resources

* [/agents/jobs](agents_jobs.md)
* [/agents/jobs/{ID}/includes](agents_jobs_id_includes.md)
* [/backupServers/{ID}](backupservers_id.md)

Methods

The following methods are supported for the /agents/jobs/{ID} resource:

* [GET /agents/jobs/{ID}](get_agents_jobs_id.md)
* [POST /agents/jobs/{ID}?action=start](post_agents_jobs_id_actionstart.md)
* [POST /agents/jobs/{ID}?action=stop](post_agents_jobs_id_actionstop.md)
* [POST /agents/jobs/{ID}?action=retry](post_agents_jobs_id_actionretry.md)
* [POST /agents/jobs/{ID}?action=toggleScheduleEnabled](post_agents_jobs_id_actiontogglescheduleenabled.md)

Resource Representation

The /agents/jobs/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="AgentBackupJobReference" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec" Name="Server Backup" UID="urn:veeam:AgentBackupJob:a6deb158-b26c-4140-8b26-5a3cc344e8ec"> |

Entity resource representation:

|  |
| --- |
| <AgentBackupJob xmlns="http://www.veeam.com/ent/v1.0" Type="AgentBackupJob" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?format=Entity" Name="Server Backup" UID="urn:veeam:AgentBackupJob:a6deb158-b26c-4140-8b26-5a3cc344e8ec">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec" Name="Server Backup" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/includes" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=toggleScheduleEnabled" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/backupSessions" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec?action=retry" />   </Links>   <JobType>AgentBackup</JobType>   <Platform>AgentForWindows</Platform>   <Description>Backup of physical server</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2020-02-12T15:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>16:00:00.0000000+01:00</Time>         <TimeOffsetUtc>2</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>2</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions>   <JobInfo>     <Includes>       <ObjectInAgentBackupJob Type="ObjectInAgentBackupJob" Href="https://srv12.tech.local:9398/api/agents/jobs/a6deb158-b26c-4140-8b26-5a3cc344e8ec/includes/51616f00-6107-48a9-95ba-1cee9ed6a86e">         <ObjectInJobId>51616f00-6107-48a9-95ba-1cee9ed6a86e</ObjectInJobId>         <Name>Windows Servers</Name>         <DisplayName>Windows Servers</DisplayName>         <GuestProcessingOptions>           <VssSnapshotOptions>             <VssSnapshotMode>RequireSuccess</VssSnapshotMode>             <IsCopyOnly>false</IsCopyOnly>           </VssSnapshotOptions>           <WindowsGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>%windir%</Path>               <Path>%ProgramFiles%</Path>               <Path>%ProgramFiles(x86)%</Path>               <Path>%ProgramW6432%</Path>               <Path>%TEMP%</Path>             </ExcludedIndexingFolders>           </WindowsGuestFSIndexingOptions>           <LinuxGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>/cdrom</Path>               <Path>/dev</Path>               <Path>/media</Path>               <Path>/mnt</Path>               <Path>/proc</Path>               <Path>/tmp</Path>               <Path>/lost+found</Path>             </ExcludedIndexingFolders>           </LinuxGuestFSIndexingOptions>           <SqlBackupOptions>             <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>             <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>             <UseDbBackupRetention>true</UseDbBackupRetention>             <RetainDays>15</RetainDays>           </SqlBackupOptions>           <WindowsCredentialsId />           <LinuxCredentialsId />         </GuestProcessingOptions>       </ObjectInAgentBackupJob>     </Includes>     <GuestProcessingOptions>       <VssSnapshotOptions>         <VssSnapshotMode>RequireSuccess</VssSnapshotMode>         <IsCopyOnly>false</IsCopyOnly>       </VssSnapshotOptions>       <WindowsGuestFSIndexingOptions>         <FileSystemIndexingMode>EveryFolders</FileSystemIndexingMode>         <IncludedIndexingFolders />         <ExcludedIndexingFolders />       </WindowsGuestFSIndexingOptions>       <LinuxGuestFSIndexingOptions>         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>         <IncludedIndexingFolders />         <ExcludedIndexingFolders />       </LinuxGuestFSIndexingOptions>       <SqlBackupOptions>         <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>         <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>         <UseDbBackupRetention>true</UseDbBackupRetention>         <RetainDays>15</RetainDays>       </SqlBackupOptions>       <WindowsCredentialsId />       <LinuxCredentialsId />     </GuestProcessingOptions>     <GfsRetentionPolicy Enabled="false">       <Weekly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedDay>Sunday</SelectedDay>       </Weekly>       <Monthly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedWeek>First</SelectedWeek>       </Monthly>       <Yearly>         <Enabled>false</Enabled>         <RetentionPeriod>1</RetentionPeriod>         <SelectedMonth>January</SelectedMonth>       </Yearly>     </GfsRetentionPolicy>     <SimpleRetentionPolicy>       <RetainCycles>5</RetainCycles>       <RetainDaysToKeep>7</RetainDaysToKeep>       <RetainLimitType>Cycles</RetainLimitType>     </SimpleRetentionPolicy>   </JobInfo> </AgentBackupJob> |


