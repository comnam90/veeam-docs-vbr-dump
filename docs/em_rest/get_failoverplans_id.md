---
title: "GET /failoverPlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_failoverplans_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /failoverPlans/{ID}


Returns a resource representation of the failover plan having the specified ID.

Request

To get a resource representation of the failover plan, send the GET HTTP request to the /failoverPlans/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/failoverPlans/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/failoverPlans/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /failoverPlans/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the failover plan, for example: urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009. |
| Name | String | Name of the failover plan, for example: SQL Failover Plan. |
| Description | String | Description specified for the failover plan. |
| FailoverPlanInfo | FailoverPlanInfoType | Contains the Includes element with a list of the FailoveredVm objects — VMs added to the failover plan. For details, see [Failover Plan VMs](#VMs). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=FailoverPlan](get_query_failoverplan.md).

Failover Plan VMs

The FailoveredVm element contains the following VM options.

Response Body

| Element | Type | Description |
| FailoveredVmId | String | ID of the VM, for example: 88792301-c3dc-495b-9505-45de8b821845. |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM, for example: urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-85541. |
| Name | String | VM name. |
| DisplayName | String | VM display name. |
| Order | Int | Failover order. |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). |

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the failover plan was created. |
| /failoverPlans/{ID} | Alternate | Alternate URL of the [/failoverPlans/{ID}](failoverplans_id.md) resource. |
| failoverPlans/{ID} | Edit | URL for the [PUT /failoverPlans/{ID}](put_failoverplans_id.md) request. |
| failoverPlans/{ID}?action=start | Start | URL for the [POST /failoverPlans/{ID}?action=start](post_failoverplans_id_start.md) request. |
| failoverPlans/{ID}?action=start | Undo | URL for the [POST /failoverPlans/{ID}?action=undo](post_failoverplans_id_undo.md) request. |

Example

The example below returns an entity representation of the failover plan having ID af8a333b-3df3-467a-b3ce-df8ac508be51:

|  |
| --- |
| Request:  GET https://localhost:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <FailoverPlan xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?format=Entity" Type="FailoverPlan" Name="Failover plan 1" UID="urn:veeam:FailoverPlan:af8a333b-3df3-467a-b3ce-df8ac508be51" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51" Name="Failover plan 1" Type="FailoverPlanReference" Rel="Alternate" />         <Link Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51" Name="Failover plan 1" Type="FailoverPlanReference" Rel="Edit" />         <Link Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?action=start" Rel="Start" />         <Link Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?action=undo" Rel="Undo" />     </Links>     <Description>Created by TECH\sheila.d.cory</Description>     <FailoverPlanInfo>         <Includes>             <FailoveredVm Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51/includes/88792301-c3dc-495b-9505-45de8b821845" Type="FailoveredVm">                 <FailoveredVmId>88792301-c3dc-495b-9505-45de8b821845</FailoveredVmId>                 <HierarchyObjRef>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-85541</HierarchyObjRef>                 <Name>ubuntu88</Name>                 <DisplayName>ubuntu88</DisplayName>                 <Order>0</Order>                 <GuestProcessingOptions>                     <VssSnapshotOptions>                         <VssSnapshotMode>RequireSuccess</VssSnapshotMode>                         <IsCopyOnly>false</IsCopyOnly>                     </VssSnapshotOptions>                     <WindowsGuestFSIndexingOptions>                         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>                         <IncludedIndexingFolders />                         <ExcludedIndexingFolders>                             <Path>%windir%</Path>                             <Path>%ProgramFiles%</Path>                             <Path>%ProgramFiles(x86)%</Path>                             <Path>%ProgramW6432%</Path>                             <Path>%TEMP%</Path>                         </ExcludedIndexingFolders>                     </WindowsGuestFSIndexingOptions>                     <LinuxGuestFSIndexingOptions>                         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>                         <IncludedIndexingFolders />                         <ExcludedIndexingFolders>                             <Path>/cdrom</Path>                             <Path>/dev</Path>                             <Path>/media</Path>                             <Path>/mnt</Path>                             <Path>/proc</Path>                             <Path>/tmp</Path>                             <Path>/lost+found</Path>                         </ExcludedIndexingFolders>                     </LinuxGuestFSIndexingOptions>                     <SqlBackupOptions>                         <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>                         <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>                         <UseDbBackupRetention>true</UseDbBackupRetention>                         <RetainDays>15</RetainDays>                     </SqlBackupOptions>                     <WindowsCredentialsId />                     <LinuxCredentialsId />                 </GuestProcessingOptions>             </FailoveredVm>             <FailoveredVm Href="https://enterprise06.tech.local:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51/includes/37530b26-03af-422d-826c-d023ea02b0eb" Type="FailoveredVm">                 <FailoveredVmId>37530b26-03af-422d-826c-d023ea02b0eb</FailoveredVmId>                 <HierarchyObjRef>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-67288</HierarchyObjRef>                 <Name>apache02</Name>                 <DisplayName>apache02</DisplayName>                 <Order>1</Order>                 <GuestProcessingOptions>                     <VssSnapshotOptions>                         <VssSnapshotMode>RequireSuccess</VssSnapshotMode>                         <IsCopyOnly>false</IsCopyOnly>                     </VssSnapshotOptions>                     <WindowsGuestFSIndexingOptions>                         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>                         <IncludedIndexingFolders />                         <ExcludedIndexingFolders>                             <Path>%windir%</Path>                             <Path>%ProgramFiles%</Path>                             <Path>%ProgramFiles(x86)%</Path>                             <Path>%ProgramW6432%</Path>                             <Path>%TEMP%</Path>                         </ExcludedIndexingFolders>                     </WindowsGuestFSIndexingOptions>                     <LinuxGuestFSIndexingOptions>                         <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>                         <IncludedIndexingFolders />                         <ExcludedIndexingFolders>                             <Path>/cdrom</Path>                             <Path>/dev</Path>                             <Path>/media</Path>                             <Path>/mnt</Path>                             <Path>/proc</Path>                             <Path>/tmp</Path>                             <Path>/lost+found</Path>                         </ExcludedIndexingFolders>                     </LinuxGuestFSIndexingOptions>                     <SqlBackupOptions>                         <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>                         <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>                         <UseDbBackupRetention>true</UseDbBackupRetention>                         <RetainDays>15</RetainDays>                     </SqlBackupOptions>                     <WindowsCredentialsId />                     <LinuxCredentialsId />                 </GuestProcessingOptions>             </FailoveredVm>         </Includes>     </FailoverPlanInfo> </FailoverPlan> |

Page updated 2026-07-29

