---
title: "GET /query?type=NasJob"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_nasjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=NasJob


Returns a resource representation of a collection of file share backup jobs created on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/nas/jobs](nas_jobs.md).

Request

To get a list of file share backup jobs, send the GET HTTP request to the query with the type parameter set to NasJob.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=NasJob |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the file share backup job, for example: urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2. |
| Name | String | Name of the file share backup job, for example: Shared Files Backup. |
| Description | String | Description of the file share backup job. |
| NextRun | DateTime | Date and time of the next job run. The parameter accepts only UTC-formatted DateTime values.  Note that this parameter can be used for scheduled jobs only. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the file share backup job resource. |
| BackupServerName | String | Name of the backup server parent to the file share backup job resource. |

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

In the response body, the REST API returns a representation of the /nas/jobs resource collection.

Example

The example below returns an entity resource representation of a collection of file share backup jobs created on the backup server enterprise06.tech.local.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=NasJob&format=Entities&filter=BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <NASJobs>       <NASJob Type="NasJob" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade?format=Entity" Name="File Backup Job 1" UID="urn:veeam:NasJob:e72c6fce-0680-4340-896f-e44903677ade">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="JobReference" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade" Name="File Backup Job 1" />           <Link Rel="Down" Type="NasObjectList" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/includes" />           <Link Rel="ToggleScheduleEnabled" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/toggleScheduleEnabled" />           <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/backupSessions" />           <Link Rel="Start" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/start" />           <Link Rel="Stop" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/stop" />           <Link Rel="Retry" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/retry" />         </Links>         <Description>Created by TECH\administrator</Description>         <Includes>           <NASObject Type="NasObject" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/includes/f33fe405-a460-415e-9ffc-d1ef2e0b6c03">             <HierarchyObjRef>urn:NasBackup:BackupServer:35ab6523-0e40-4d92-a0ea-11465791cd91</HierarchyObjRef>             <ObjectInJobId>f33fe405-a460-415e-9ffc-d1ef2e0b6c03</ObjectInJobId>             <FileOrFolder>winsrv88.tech.local:/nfs\_share</FileOrFolder>             <FileServerUid>urn:veeam:FileServer:1131bc00-36c0-4355-87fc-7f748aceb978</FileServerUid>             <InclusionMask>               <Extension>\*.\*</Extension>             </InclusionMask>           </NASObject>         </Includes>         <StorageOptions>           <BackupRepositoryUid>urn:veeam:Repository:88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec</BackupRepositoryUid>           <ShorttermRetentionType>Day</ShorttermRetentionType>           <ShorttermRetentionPeriod>21</ShorttermRetentionPeriod>           <LongtermRetentionEnabled>false</LongtermRetentionEnabled>           <AdvancedStorageOptions>             <ACL>               <FileAttributesChangeTrackingMode>TrackOnlyFolderAttributesChanges</FileAttributesChangeTrackingMode>             </ACL>           </AdvancedStorageOptions>         </StorageOptions>         <ScheduleConfigured>true</ScheduleConfigured>         <ScheduleEnabled>true</ScheduleEnabled>         <JobScheduleOptions>           <Standart>             <RetryOptions>               <RetryTimes>3</RetryTimes>               <RetryTimeout>10</RetryTimeout>               <RetrySpecified>true</RetrySpecified>             </RetryOptions>             <WaitForBackupCompletion>true</WaitForBackupCompletion>             <BackupCompetitionWaitingPeriodMin>180</BackupCompetitionWaitingPeriodMin>             <OptionsDaily Enabled="false">               <Kind>Everyday</Kind>               <Days>Sunday</Days>               <Days>Monday</Days>               <Days>Tuesday</Days>               <Days>Wednesday</Days>               <Days>Thursday</Days>               <Days>Friday</Days>               <Days>Saturday</Days>               <Time>06:00:00.0000000+02:00</Time>               <TimeOffsetUtc>1</TimeOffsetUtc>             </OptionsDaily>             <OptionsMonthly Enabled="false">               <Time>06:00:00.0000000+02:00</Time>               <TimeOffsetUtc>1</TimeOffsetUtc>               <DayNumberInMonth>Fourth</DayNumberInMonth>               <DayOfWeek>Saturday</DayOfWeek>               <Months>January</Months>               <Months>February</Months>               <Months>March</Months>               <Months>April</Months>               <Months>May</Months>               <Months>June</Months>               <Months>July</Months>               <Months>August</Months>               <Months>September</Months>               <Months>October</Months>               <Months>November</Months>               <Months>December</Months>               <DayOfMonth>1</DayOfMonth>             </OptionsMonthly>             <OptionsPeriodically Enabled="false">               <Kind>Hours</Kind>               <FullPeriod>1</FullPeriod>               <Schedule>                 <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>               </Schedule>             </OptionsPeriodically>             <OptionsContinuous Enabled="false">               <Schedule>                 <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>               </Schedule>             </OptionsContinuous>             <OptionsBackupWindow Enabled="false">               <TimePeriods>                 <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>               </TimePeriods>             </OptionsBackupWindow>             <OptionsDaisyChaining Enabled="true">               <PreviousJobUid>urn:veeam:Job:c05dfa57-f59a-4e90-8065-b7f5d3276406</PreviousJobUid>             </OptionsDaisyChaining>           </Standart>         </JobScheduleOptions>       </NASJob>     </NASJobs>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=NasJob&format=Entities&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=NasJob&format=Entities&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

