---
title: "GET /nas/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas/jobs/{ID}


Returns a resource representation of the file share backup job resource having the specified ID. The file share backup job is configured in Veeam Backup & Replication.

Request

To get a resource representation of the file share backup job, send the GET HTTP request to the /nas/jobs/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /nas/jobs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the file share backup job, for example: urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2. |
| Name | String | Name of the file share backup job, for example: Shared Files Backup. |
| Description | String | Description of the file share backup job. |
| Includes | NASObjectListType | Includes a list of file shares processed by the job. For details, see [GET /nas/jobs/{ID}/includes](get_nas_jobs_id_includes.md). |
| StorageOptions | NASJobStorageOptionsInfoType | Defines backup and archive repositories where the file share backup job must store backup files, and settings for moving files and folders to these repositories. For details, see [Storage Options](#storageoptions). |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| JobScheduleOptions | ScheduleOptionsInfoType | Options that define the schedule by which the job runs. For details, see [Job Scheduling Options](jobscheduleoptions.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=NasJob](get_query_nasjob.md).

Storage Options

The StorageOptions element contains the following storage options.

Response Body

| Element | Type | Description |
| BackupRepositoryUid | UidType | UID of the backup repository where backup files must be stored, for example: urn:veeam:Repository:88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec. |
| ShorttermRetentionType | String | Retention policy type for the short-term repository. Possible values:   * Day * Month |
| ShorttermRetentionPeriod | Int | Time period to keep data in the backup repository. When this period is passed, Veeam Backup & Replication moves data to the archive repository if the long-term retention is enabled. |
| LongtermRetentionEnabled | Boolean | Defines whether the long-term retention is enabled. Possible values:   * True * False |
| KeepFileVersionsHistoryOptions | NASJobStorageKeepFileVersionsHistory OptionsInfoType | Archiving settings. For details, see [Long-Term Retention Settings](#ltr). |
| NASJobAdvancedStorageOptions | NASJobAdvancedStorageOptionsInfoType | Advanced storage settings. For details, see [Advanced Storage Settings](#advanced). |

Long-Term Retention Settings

The KeepFileVersionsHistoryOptions element contains the following archiving settings.

Response Body

| Element | Type | Description |
| LongtermRetentionType | String | Retention policy type for the short-term repository. Possible values:   * Month * Year |
| LongtermRetentionPeriod | Int | Time period to keep data in the backup repository. When this period is passed, Veeam Backup & Replication moves data to the archive repository if the long-term retention is enabled. |
| BackupRepositoryUid | UidType | UID of the archive repository where backup files must be stored, for example: urn:veeam:Repository:d4b5e196-f3ad-474c-99bc-dfef051dae07. |
| ArchiveFileTypes | NASLongTermArchivalOptionsInfoType | Files that must be archived or excluded from the archive. For detail, see [Long-Term Archival Options](#lta). |

Long-Term Archival Options

The ArchiveFileTypes element contains the following long-term archival options.

Response Body

| Element | Type | Description |
| ActiveFileRetentionEnabled | Boolean | Defines whether retention for active files (files currently existing in the source file share) is enabled. Possible values:   * True * False |
| MaxActiveFileVersionsToKeep | Int | Number of versions to be stored for active files. |
| DeletedFileRetentionEnabled | Boolean | Defines whether retention for deleted files (files deleted from the source file share) is enabled. Possible values:   * True * False |
| MaxDeletedFileVersionsToKeep | Int | Number of versions to be stored for deleted files. |
| FileExtensionsOption | NASJobFileExtensionsOptionsInfoType | Defines extensions of files that must be archived or excluded from the archive. For detail, see [File Extensions](#fileextensions). |

File Extensions

The FileExtensionsOption element contains the following file extensions options.

Response Body

| Element | Type | Description |
| ArchiveFileExtensionsScope | String | Type of the file scope. Possible values   * Any * Specified * ExceptSpecified |
| InclusionMask | FileExtensionInfoListType | File extensions for files to be archived. Represents a list of string Extension parameters. |
| ExclusionMask | FileExtensionInfoListType | File extensions for files to be excluded from the archive. Represents a list of string Extension parameters. |

Advanced Storage Settings

The NASJobAdvancedStorageOptions element contains the following advanced storage settings.

Response Body

| Element | Type | Description |
| ACL | NASJobAdvancedStorageOptionsSecurityOptionsInfoType | Defines how the backup job processes permissions and attributes. Consists of the string FileAttributesChangeTrackingMode parameter. Possible values:   * TrackOnlyFolderAttributesChanges * TrackEverythingAttributesChanges |

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the file share backup job was created. |
| /nas/jobs/{ID} | Alternate | Alternate URL of the [/nas/jobs/{ID}](nas_jobs_id.md) resource. |
| /nas/jobs/{ID}/includes | Down | URL of the [/nas/jobs/{ID}/includes](nas_jobs_id_includes.md) resource — a collection of files and folders processed by the file share backup job. |
| /nas/jobs/{ID}/toggleScheduleEnabled | ToggleScheduleEnabled | URL for the [POST /nas/jobs/{ID}/toggleScheduleEnabled](post_nas_jobs_id_actiontogglescheduleenabled.md) request. |
| /nas/jobs/{ID}/backupSessions | Down | URL of the [/nas/jobs/{ID}/backupSessions](nas_jobs_id_backupsessions.md) resource — a collection of backup job sessions performed for the file share backup job. |
| /nas/jobs/{ID}/Start | Start | URL for the [POST /nas/jobs/{ID}/start](post_nas_jobs_id_actionstart.md) request. |
| /nas/jobs/{ID}/Stop | Stop | URL for the [POST /nas/jobs/{ID}/stop](post_nas_jobs_id_actionstop.md) request. |
| /nas/jobs/{ID}/Retry | Retry | URL for the [POST /nas/jobs/{ID}/retry](post_nas_jobs_id_actionretry.md) request. |

Example

The example below returns an entity resource representation of the file share backup job having ID 93dfbb3e-f420-45cf-addc-4ee9297113f2.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <NASJob xmlns="http://www.veeam.com/ent/v1.0" Type="NasJob" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="JobReference" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />     <Link Rel="Down" Type="NasObjectList" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes" />     <Link Rel="ToggleScheduleEnabled" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/toggleScheduleEnabled" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/backupSessions" />     <Link Rel="Start" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/start" />     <Link Rel="Stop" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/stop" />     <Link Rel="Retry" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/retry" />   </Links>   <Description>Backup of file share</Description>   <Includes>     <NASObject Type="NasObject" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes/6fefb504-856d-4c31-b767-76af5567c407">       <HierarchyObjRef>urn:NasBackup:BackupServer:5735d1af-3aad-49ac-ac77-eab708ac1a37</HierarchyObjRef>       <ObjectInJobId>6fefb504-856d-4c31-b767-76af5567c407</ObjectInJobId>       <FileOrFolder>\\srv12\share</FileOrFolder>       <FileServerUid>urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c</FileServerUid>       <InclusionMask>         <Extension>\*.\*</Extension>       </InclusionMask>       <ExclusionMask>         <Extension>\\srv12\share\.snapshot</Extension>         <Extension>\\srv12\share\~snapshot</Extension>       </ExclusionMask>     </NASObject>   </Includes>   <StorageOptions>     <BackupRepositoryUid>urn:veeam:Repository:efdea468-7d1d-4b63-8246-31b83849880d</BackupRepositoryUid>     <ShorttermRetentionType>Day</ShorttermRetentionType>     <ShorttermRetentionPeriod>3</ShorttermRetentionPeriod>     <LongtermRetentionEnabled>false</LongtermRetentionEnabled>     <AdvancedStorageOptions>       <ACL>         <FileAttributesChangeTrackingMode>TrackOnlyFolderAttributesChanges</FileAttributesChangeTrackingMode>       </ACL>     </AdvancedStorageOptions>   </StorageOptions>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2025-01-31T15:00:00Z</NextRun>   <JobScheduleOptions>     <Standart>       <RetryOptions>         <RetryTimes>3</RetryTimes>         <RetryTimeout>10</RetryTimeout>         <RetrySpecified>true</RetrySpecified>       </RetryOptions>       <WaitForBackupCompletion>true</WaitForBackupCompletion>       <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>       <OptionsDaily Enabled="true">         <Kind>Everyday</Kind>         <Days>Sunday</Days>         <Days>Monday</Days>         <Days>Tuesday</Days>         <Days>Wednesday</Days>         <Days>Thursday</Days>         <Days>Friday</Days>         <Days>Saturday</Days>         <Time>16:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>       </OptionsDaily>       <OptionsMonthly Enabled="false">         <Time>22:00:00.0000000+01:00</Time>         <TimeOffsetUtc>1</TimeOffsetUtc>         <DayNumberInMonth>Fourth</DayNumberInMonth>         <DayOfWeek>Saturday</DayOfWeek>         <Months>January</Months>         <Months>February</Months>         <Months>March</Months>         <Months>April</Months>         <Months>May</Months>         <Months>June</Months>         <Months>July</Months>         <Months>August</Months>         <Months>September</Months>         <Months>October</Months>         <Months>November</Months>         <Months>December</Months>         <DayOfMonth>1</DayOfMonth>       </OptionsMonthly>       <OptionsPeriodically Enabled="false">         <Kind>Hours</Kind>         <FullPeriod>1</FullPeriod>         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsPeriodically>       <OptionsContinuous Enabled="false">         <Schedule>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </Schedule>       </OptionsContinuous>       <OptionsBackupWindow Enabled="false">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </OptionsBackupWindow>       <OptionsDaisyChaining Enabled="false">         <PreviousJobUid />       </OptionsDaisyChaining>     </Standart>   </JobScheduleOptions> </NASJob> |

Page updated 2026-07-29

