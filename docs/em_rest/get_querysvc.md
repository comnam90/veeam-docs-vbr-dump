---
title: "GET /querySvc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_querysvc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /querySvc


Returns a list of queries for entity resources.

Request

To get a list of queries, send the GET HTTP request to the /querySvc resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/querySvc |

Request Header

The request contains the following headers:

Request Header

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

In the response body, the REST API returns a representation of the /querySvc resource.

Example

The example below returns a resource representation of the /querySvc resource.

|  |
| --- |
| Request:  GET https://localhost:9398/api/querySvc  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QuerySvc xmlns="http://www.veeam.com/ent/v1.0" Type="QueryService" Href="https://localhost:9398/api/querySvc">   <Links>     <Link Rel="Up" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/ff9abda1-d795-437a-9f0a-6a343e1dc768" />     <Link Rel="Down" Type="VmRestorePointList" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="VAppRestorePointList" Href="https://localhost:9398/api/query?type=VAppRestorePoint&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="VmReplicaPointList" Href="https://localhost:9398/api/query?type=VmReplicaPoint&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="TaskList" Href="https://localhost:9398/api/query?type=Task&format=Entities&sortAsc=TaskUid&pageSize=15&page=1" />     <Link Rel="Down" Type="JobList" Href="https://localhost:9398/api/query?type=Job&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="RestorePointList" Href="https://localhost:9398/api/query?type=RestorePoint&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="BackupTaskSessionList" Href="https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="ReplicaTaskSessionList" Href="https://localhost:9398/api/query?type=ReplicaTaskSession&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="RestoreSessionList" Href="https://localhost:9398/api/query?type=RestoreSession&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="RepositoryList" Href="https://localhost:9398/api/query?type=Repository&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="BackupList" Href="https://localhost:9398/api/query?type=Backup&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="ReplicaList" Href="https://localhost:9398/api/query?type=Replica&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="HierarchyRootList" Href="https://localhost:9398/api/query?type=HierarchyRoot&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://localhost:9398/api/query?type=BackupJobSession&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="ReplicaJobSessionList" Href="https://localhost:9398/api/query?type=ReplicaJobSession&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="BackupServerList" Href="https://localhost:9398/api/query?type=BackupServer&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="ManagedServerList" Href="https://localhost:9398/api/query?type=ManagedServer&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="FailoverPlanList" Href="https://localhost:9398/api/query?type=FailoverPlan&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="WanAcceleratorList" Href="https://localhost:9398/api/query?type=WanAccelerator&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudGatewayList" Href="https://localhost:9398/api/query?type=CloudGateway&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudTenantList" Href="https://localhost:9398/api/query?type=CloudTenant&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/query?type=Passwords&format=Entities&sortAsc=BackupServerUid&pageSize=15&page=1" />     <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/query?type=Credentials&format=Entities&sortAsc=BackupServerUid&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudReplicaList" Href="https://localhost:9398/api/query?type=CloudReplica&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="BackupFileList" Href="https://localhost:9398/api/query?type=BackupFile&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="VCloudOrganizationConfigList" Href="https://localhost:9398/api/query?type=VCloudOrganizationConfig&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudSubtenantList" Href="https://localhost:9398/api/query?type=CloudSubtenant&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudHardwarePlanList" Href="https://localhost:9398/api/query?type=CloudHardwarePlan&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudPublicIpAddressList" Href="https://localhost:9398/api/query?type=CloudPublicIpAddress&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="AgentBackupJobList" Href="https://localhost:9398/api/query?type=AgentBackupJob&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="AgentRestorePointList" Href="https://localhost:9398/api/query?type=AgentRestorePoint&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="AgentProtectionGroupList" Href="https://localhost:9398/api/query?type=AgentProtectionGroup&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="DiscoveredComputerList" Href="https://localhost:9398/api/query?type=DiscoveredComputer&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudFailoverPlanList" Href="https://localhost:9398/api/query?type=CloudFailoverPlan&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="CloudGatewayPoolList" Href="https://localhost:9398/api/query?type=CloudGatewayPool&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="VSphereSelfServiceConfigList" Href="https://localhost:9398/api/query?type=VSphereSelfServiceConfig&format=Entities&sortAsc=Name&pageSize=15&page=1" />     <Link Rel="Down" Type="ExternalRepositoryList" Href="https://localhost:9398/api/query?type=ExternalRepository&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="NasJobList" Href="https://localhost:9398/api/query?type=NasJob&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="FileServerList" Href="https://localhost:9398/api/query?type=FileServer&format=Entities&sortAsc=name&pageSize=15&page=1" />     <Link Rel="Down" Type="VAppReplicaPointList" Href="https://localhost:9398/api/query?type=VAppReplicaPoint&format=Entities&sortAsc=name&pageSize=15&page=1" />   </Links> </QuerySvc> |

Page updated 2026-07-29

