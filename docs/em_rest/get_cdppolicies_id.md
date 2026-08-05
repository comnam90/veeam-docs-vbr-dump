---
title: "GET /cdpPolicies/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdppolicies_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpPolicies/{ID}


Returns a resource representation of the CDP policy resource having the specified ID.

Request

To get a resource representation of the CDP policy, send the GET HTTP request to the /cdpPolicies/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cdpPolicies/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the CDP policy, for example: urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877. |
| Name | String | Name of the CDP policy, for example: CDP Policy 1. |
| PolicyType | String | Policy type. Possible value: CdpReplica. |
| Platform | String | Platform for which the job is created. Possible values:   * VMware * vCloud |
| Description | String | Description of the CDP policy. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the CDP policy. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the CDP policy. Possible values:   * True * False |
| NextRun | DateTime | Date and time of the next run of the CDP policy. The parameter accepts only UTC-formatted DateTime values. |
| PolicyScheduleOptions | ScheduleOptionsInfoType | Options that define the schedule by which the CDP policy runs. For details, see [Policy Scheduling Options](policyscheduleoptions.md). |
| CdpPolicyInfo | — | Complex object that includes a collection of VMs and VM containers processed by the CDP policy. For details, see [GET /cdpPolicies/{ID}/includes](get_cdppolicies_id_includes.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CdpPolicy](get_query_cdppolicy.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpPolicies/{ID} | Alternate | Alternate URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource. |
| /cdpPolicies/{ID} | Edit | URL for the [PUT /cdpPolicies/{ID}](put_cdppolicies_id.md) request. |
| /cdpPolicies/{ID}?action=disable | Disable | URL for the [POST /cdpPolicies/{ID}?action=disable](post_cdppolicies_id_actiondisable.md) request. |
| /cdpPolicies/{ID}?action=enable | Enable | URL for the [POST /cdpPolicies/{ID}&action=enable](post_cdppolicies_id_actionenable.md) request. |
| /cdpPolicies/{ID}/includes | Down | URL of the [/cdpPolicies/{ID}/includes](cdppolicies_id_includes.md) resource — a collection of VMs and VM containers processed by the CDP policy. |
| /cdpPolicies/{ID}/includes | Create | URL for the [POST /cdpPolicies/{ID}/includes](post_cdppolicies_id_includes.md) request. |
| /cdpPolicies/{ID}/cdpReplicaSessions | Down | URL of the [/cdpPolicies/{ID}/cdpReplicaSessions](cdppolicies_id_cdpreplicasessions.md) resource — a collection of CDP replication sessions of the CDP policy. |

Example

The example below returns an entity resource representation of the CDP policy having ID bc933bb6-0cc5-47b6-a1ec-e062b9e29877.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CdpPolicy xmlns="http://www.veeam.com/ent/v1.0" Type="CdpPolicy" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877?format=Entity" Name="CDP Policy 1" UID="urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Alternate" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877" Name="CDP Policy 1" />     <Link Rel="Edit" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877" Name="CDP Policy 1" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes" />     <Link Rel="Create" Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes" />     <Link Rel="Down" Type="CdpReplicaSessionReferenceList" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/cdpReplicaSessions" />     <Link Rel="Disable" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877?action=disable" />   </Links>   <PolicyType>CdpReplica</PolicyType>   <Platform>VMware</Platform>   <Description>Created by ENTERPRISE03\Administrator</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2025-02-10T22:39:34.827Z</NextRun>   <PolicyScheduleOptions>     <CdpReplica>       <RecoveryPointObjectiveSeconds>15</RecoveryPointObjectiveSeconds>       <RecoveryPointObjectiveMinutes>0</RecoveryPointObjectiveMinutes>       <RPOSchedule Enabled="true">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </RPOSchedule>       <RPOReporting>         <MarkAsWarning>           <Enabled>true</Enabled>           <RPOThresholdSeconds>2</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsWarning>         <MarkAsFailed>           <Enabled>true</Enabled>           <RPOThresholdSeconds>3</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsFailed>       </RPOReporting>       <ShortTermRetentionMinutes>0</ShortTermRetentionMinutes>       <ShortTermRetentionHours>4</ShortTermRetentionHours>       <LongTermRetentionHours>8</LongTermRetentionHours>       <LongTermRetentionKeepDays>7</LongTermRetentionKeepDays>       <LongTermRetentionSchedule Enabled="true">         <TimePeriods>           <Day Name="Sunday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Monday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Tuesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Wednesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Thursday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Friday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Saturday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>         </TimePeriods>       </LongTermRetentionSchedule>     </CdpReplica>   </PolicyScheduleOptions>   <CdpPolicyInfo>     <CdpReplicaPolicyInfo>       <Includes>         <ObjectInJob Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes/460ab29f-c659-4f50-955d-643a370b3744">           <ObjectInJobId>460ab29f-c659-4f50-955d-643a370b3744</ObjectInJobId>           <HierarchyObjRef>urn:VMware:Vm:45237d2c-c163-4cb1-9f6e-c9913cdea868.vm-19</HierarchyObjRef>           <Name>virt03-vm01</Name>           <DisplayName>virt03-vm01</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>true</IsCopyOnly>               <UsePersistentGuestAgent>false</UsePersistentGuestAgent>             </VssSnapshotOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>       </Includes>       <GuestProcessingOptions>         <VssSnapshotOptions>           <VssSnapshotMode>Disabled</VssSnapshotMode>           <IsCopyOnly>true</IsCopyOnly>         </VssSnapshotOptions>         <WindowsCredentialsId />         <LinuxCredentialsId />       </GuestProcessingOptions>     </CdpReplicaPolicyInfo>   </CdpPolicyInfo> </CdpPolicy> |

Page updated 2026-07-28

