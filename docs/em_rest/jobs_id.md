---
title: "/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobs_id.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---

# /jobs/{ID}


Represents a job having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/jobSessions](backupsessions.md)

Methods

The following methods are supported for the /jobs/{ID} resource:

* [GET /jobs/{ID}](get_jobs_id.md)
* [PUT /jobs/{ID}?action=edit](put_jobs_id_actionedit.md)
* [POST /jobs/{ID}?action=start](post_jobs_id_actionstart.md)
* [POST /jobs/{ID}?action=sync](post_jobs_id_actionsync.md)
* [POST /jobs/{ID}?action=stop](post_jobs_id_actionstop.md)
* [POST /jobs/{ID}?action=retry](post_jobs_id_actionretry.md)
* [POST /jobs/{ID}?action=clone](post_jobs_id_actionclone.md)
* [POST /jobs/{ID}?action=toggleScheduleEnabled](post_jobs_id_actiontogglescheduleenabled.md)

Resource Representation

The /jobs/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e" Name="DB Backup" UID="urn:veeam:Job:5658281f-625e-4627-89dd-d2a0c48be99e"> |

Entity resource representation:

|  |
| --- |
| <Job xmlns="http://www.veeam.com/ent/v1.0" Type="Job" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?format=Entity" Name="DB Backup" UID="urn:veeam:Job:5658281f-625e-4627-89dd-d2a0c48be99e">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e" Name="DB Backup" />     <Link Rel="Edit" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e" Name="DB Backup" />     <Link Rel="Clone" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=clone" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=toggleScheduleEnabled" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/backupSessions" />     <Link Rel="Create" Type="ObjectInJob" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e?action=retry" />   </Links>   <JobType>Backup</JobType>   <Platform>HyperV</Platform>   <Description>Backup of MS SQL Server DB</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2020-02-01T17:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>18:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions>   <JobInfo>     <BackupJobInfo>       <Includes>         <ObjectInJob Type="ObjectInJob" Href="https://srv12.tech.local:9398/api/jobs/5658281f-625e-4627-89dd-d2a0c48be99e/includes/0493ea16-2c1f-4d02-b74b-994bd438b89a">           <ObjectInJobId>0493ea16-2c1f-4d02-b74b-994bd438b89a</ObjectInJobId>           <HierarchyObjRef>urn:HyperV:Vm:8e7fef9f-87a8-48b4-bed1-632c3035a1a1.020aa5ab-3523-4946-b658-b8ad5b372439</HierarchyObjRef>           <Name>sqlsrv03</Name>           <DisplayName>sqlsrv03</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>false</IsCopyOnly>               <UsePersistentGuestAgent>false</UsePersistentGuestAgent>             </VssSnapshotOptions>             <WindowsGuestFSIndexingOptions>               <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>               <IncludedIndexingFolders />               <ExcludedIndexingFolders>                 <Path>%windir%</Path>                 <Path>%ProgramFiles%</Path>                 <Path>%ProgramFiles(x86)%</Path>                 <Path>%ProgramW6432%</Path>                 <Path>%TEMP%</Path>               </ExcludedIndexingFolders>             </WindowsGuestFSIndexingOptions>             <LinuxGuestFSIndexingOptions>               <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>               <IncludedIndexingFolders />               <ExcludedIndexingFolders>                 <Path>/cdrom</Path>                 <Path>/dev</Path>                 <Path>/media</Path>                 <Path>/mnt</Path>                 <Path>/proc</Path>                 <Path>/tmp</Path>                 <Path>/lost+found</Path>               </ExcludedIndexingFolders>             </LinuxGuestFSIndexingOptions>             <SqlBackupOptions>               <TransactionLogsProcessing>Backup</TransactionLogsProcessing>               <BackupLogsFrequencyMin>60</BackupLogsFrequencyMin>               <UseDbBackupRetention>false</UseDbBackupRetention>               <RetainDays>5</RetainDays>             </SqlBackupOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>       </Includes>       <GuestProcessingOptions>         <VssSnapshotOptions>           <VssSnapshotMode>RequireSuccess</VssSnapshotMode>           <IsCopyOnly>false</IsCopyOnly>         </VssSnapshotOptions>         <WindowsGuestFSIndexingOptions>           <FileSystemIndexingMode>EveryFolders</FileSystemIndexingMode>           <IncludedIndexingFolders />           <ExcludedIndexingFolders />         </WindowsGuestFSIndexingOptions>         <LinuxGuestFSIndexingOptions>           <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>           <IncludedIndexingFolders />           <ExcludedIndexingFolders />         </LinuxGuestFSIndexingOptions>         <SqlBackupOptions>           <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>           <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>           <UseDbBackupRetention>true</UseDbBackupRetention>           <RetainDays>15</RetainDays>         </SqlBackupOptions>         <WindowsCredentialsId>7255bb17-aa93-44d0-9a24-00b9cd1da6c4</WindowsCredentialsId>         <LinuxCredentialsId />       </GuestProcessingOptions>       <AdvancedStorageOptions>         <PasswordKeyId>3d152e9d-a473-4990-bc2f-27710833ba20</PasswordKeyId>       </AdvancedStorageOptions>       <GfsRetentionPolicy Enabled="true">         <Weekly>           <Enabled>true</Enabled>           <RetentionPeriod>2</RetentionPeriod>           <SelectedDay>Sunday</SelectedDay>         </Weekly>         <Monthly>           <Enabled>true</Enabled>           <RetentionPeriod>3</RetentionPeriod>           <SelectedWeek>First</SelectedWeek>         </Monthly>         <Yearly>           <Enabled>true</Enabled>           <RetentionPeriod>1</RetentionPeriod>           <SelectedMonth>January</SelectedMonth>         </Yearly>       </GfsRetentionPolicy>       <SimpleRetentionPolicy>         <RetainCycles>5</RetainCycles>         <RetainDaysToKeep>7</RetainDaysToKeep>         <RetainLimitType>Cycles</RetainLimitType>       </SimpleRetentionPolicy>     </BackupJobInfo>   </JobInfo> </Job> |


