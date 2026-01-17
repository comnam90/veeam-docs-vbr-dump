---
title: "/nas/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a file share backup job having the specified ID. The file share backup job is configured in Veeam Backup & Replication on the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}?format=Entity |

Related Resources

* [/nas/jobs](nas_jobs.md)
* [/backupServers/{ID}](backupservers_id.md)
* [/nas/jobs/{ID}/backupSessions](nas_jobs_id_backupsessions.md)

Methods

The following methods are supported for the /nas/jobs/{ID} resource:

* [GET /nas/jobs/{ID}](get_nas_jobs_id.md)
* [POST /nas/jobs/{ID}/start](post_nas_jobs_id_actionstart.md)
* [POST /nas/jobs/{ID}/stop](post_nas_jobs_id_actionstop.md)
* [POST /nas/jobs/{ID}/retry](post_nas_jobs_id_actionretry.md)
* [POST /nas/jobs/{ID}/toggleScheduleEnabled](post_nas_jobs_id_actiontogglescheduleenabled.md)

Resource Representation

The /nas/jobs/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="NasJobReference" Href="https://srv12.tech.local:9398/api/agents/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2"> |

Entity resource representation:

|  |
| --- |
| <NASJob xmlns="http://www.veeam.com/ent/v1.0" Type="NasJob" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />     <Link Rel="Down" Type="NasObjectList" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/toggleScheduleEnabled" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/backupSessions" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/retry" />   </Links>   <Description>Backup of file share</Description>   <Includes>     <NASObject Type="NasObject" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes/6fefb504-856d-4c31-b767-76af5567c407">       <HierarchyObjRef>urn:NasBackup:BackupServer:5735d1af-3aad-49ac-ac77-eab708ac1a37</HierarchyObjRef>       <ObjectInJobId>6fefb504-856d-4c31-b767-76af5567c407</ObjectInJobId>       <FileOrFolder>\\srv12\share</FileOrFolder>       <FileServerUid>urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c</FileServerUid>       <InclusionMask>         <Extension>\*.\*</Extension>       </InclusionMask>       <ExclusionMask>         <Extension>\\srv12\share\.snapshot</Extension>         <Extension>\\srv12\share\~snapshot</Extension>       </ExclusionMask>     </NASObject>   </Includes>   <StorageOptions>     <BackupRepositoryUid>urn:veeam:Repository:efdea468-7d1d-4b63-8246-31b83849880d</BackupRepositoryUid>     <ShorttermRetentionType>Day</ShorttermRetentionType>     <ShorttermRetentionPeriod>3</ShorttermRetentionPeriod>     <LongtermRetentionEnabled>false</LongtermRetentionEnabled>     <AdvancedStorageOptions>       <ACL>         <FileAttributesChangeTrackingMode>TrackOnlyFolderAttributesChanges</FileAttributesChangeTrackingMode>       </ACL>     </AdvancedStorageOptions>   </StorageOptions>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2020-01-31T15:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>16:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions> </NASJob> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
