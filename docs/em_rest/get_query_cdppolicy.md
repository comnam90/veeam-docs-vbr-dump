---
title: "GET /query?type=CdpPolicy"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdppolicy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CdpPolicy


Returns a collection of CDP policies created on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/cdpPolicies](cdppolicies.md).

Request

To get a list of CDP policies, send the GET HTTP request to the query with the type parameter set to CdpPolicy.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpPolicy |

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
| UID | UidType | UID of the CDP policy, for example: urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877. |
| Name | String | Name of the CDP policy, for example: CDP Policy 1. |
| Description | String | Description of the CDP policy. |
| NextRun | DateTime | Date and time of the next run of the CDP policy. The parameter accepts only UTC-formatted DateTime values. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the CDP policy. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the CDP policy. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the CDP policy resource. |
| BackupServerName | String | Name of the backup server parent to the CDP policy resource. |

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

In the response body, the REST API returns a representation of the /cdpPolicies resource collection.

Example

The example below returns an entity resource representation of a collection of CDP policies created on the backupsrv29.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=cdpPolicy&format=Entities&filter=BackupServerName=="backupsrv29.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CdpPolicies>       <CdpPolicy Type="CdpPolicy" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33?format=Entity" Name="CDP Policy" UID="urn:veeam:CdpPolicy:872a3860-3805-43b8-bcf6-388384bfed33">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Alternate" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33" Name="CDP Policy" />           <Link Rel="Edit" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33" Name="CDP Policy" />           <Link Rel="Down" Type="ObjectInJobList" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/includes" />           <Link Rel="Create" Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/includes" />           <Link Rel="Down" Type="CdpReplicaSessionReferenceList" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/cdpReplicaSessions" />           <Link Rel="Disable" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33?action=disable" />         </Links>         <PolicyType>CdpReplica</PolicyType>         <Platform>VMware</Platform>         <Description />         <ScheduleConfigured>true</ScheduleConfigured>         <ScheduleEnabled>true</ScheduleEnabled>         <NextRun>2025-06-01T13:41:20.68Z</NextRun>         <PolicyScheduleOptions>           <CdpReplica>             <RecoveryPointObjectiveSeconds>15</RecoveryPointObjectiveSeconds>             <RecoveryPointObjectiveMinutes>0</RecoveryPointObjectiveMinutes>             <RPOSchedule Enabled="true">               <TimePeriods>                 <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>                 <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>               </TimePeriods>             </RPOSchedule>             <RPOReporting>               <MarkAsWarning>                 <Enabled>true</Enabled>                 <RPOThresholdSeconds>2</RPOThresholdSeconds>                 <RPOThresholdMinutes>0</RPOThresholdMinutes>               </MarkAsWarning>               <MarkAsFailed>                 <Enabled>true</Enabled>                 <RPOThresholdSeconds>3</RPOThresholdSeconds>                 <RPOThresholdMinutes>0</RPOThresholdMinutes>               </MarkAsFailed>             </RPOReporting>             <ShortTermRetentionMinutes>0</ShortTermRetentionMinutes>             <ShortTermRetentionHours>4</ShortTermRetentionHours>             <LongTermRetentionHours>8</LongTermRetentionHours>             <LongTermRetentionKeepDays>7</LongTermRetentionKeepDays>             <LongTermRetentionSchedule Enabled="true">               <TimePeriods>                 <Day Name="Sunday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Monday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Tuesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Wednesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Thursday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Friday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>                 <Day Name="Saturday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>               </TimePeriods>             </LongTermRetentionSchedule>           </CdpReplica>         </PolicyScheduleOptions>         <CdpPolicyInfo>           <CdpReplicaPolicyInfo>             <Includes>               <ObjectInJob Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/includes/7493cec7-e8d9-4d88-b5e9-8fc651370462">                 <ObjectInJobId>7493cec7-e8d9-4d88-b5e9-8fc651370462</ObjectInJobId>                 <HierarchyObjRef>urn:VMware:Vm:83963a7e-d43f-4fea-9036-466898c9c9e7.vm-84375</HierarchyObjRef>                 <Name>virt03-vm01</Name>                 <DisplayName>virt03-vm01</DisplayName>                 <GuestProcessingOptions>                   <VssSnapshotOptions>                     <VssSnapshotMode>RequireSuccess</VssSnapshotMode>                     <IsCopyOnly>true</IsCopyOnly>                   </VssSnapshotOptions>                   <WindowsCredentialsId />                   <LinuxCredentialsId />                 </GuestProcessingOptions>               </ObjectInJob>               <ObjectInJob Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/includes/82a49ecf-081e-4eca-b6ee-1df01decf16e">                 <ObjectInJobId>82a49ecf-081e-4eca-b6ee-1df01decf16e</ObjectInJobId>                 <HierarchyObjRef>urn:VMware:Vm:83963a7e-d43f-4fea-9036-466898c9c9e7.vm-84373</HierarchyObjRef>                 <Name>virt03-ubuntu01</Name>                 <DisplayName>virt03-ubuntu01</DisplayName>                 <GuestProcessingOptions>                   <VssSnapshotOptions>                     <VssSnapshotMode>RequireSuccess</VssSnapshotMode>                     <IsCopyOnly>false</IsCopyOnly>                   </VssSnapshotOptions>                   <WindowsCredentialsId />                   <LinuxCredentialsId />                 </GuestProcessingOptions>               </ObjectInJob>             </Includes>             <GuestProcessingOptions>               <VssSnapshotOptions>                 <VssSnapshotMode>Disabled</VssSnapshotMode>                 <IsCopyOnly>true</IsCopyOnly>               </VssSnapshotOptions>               <WindowsCredentialsId />               <LinuxCredentialsId />             </GuestProcessingOptions>           </CdpReplicaPolicyInfo>         </CdpPolicyInfo>       </CdpPolicy>     </CdpPolicies>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=cdpPolicy&format=Entities&filter=BackupServerName=="backupsrv29.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=cdpPolicy&format=Entities&filter=BackupServerName=="backupsrv29.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

