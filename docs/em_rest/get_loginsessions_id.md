---
title: "GET /logonSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_loginsessions_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /logonSessions/{ID}


Returns a currently existing logon session having the specified ID.

Request

To get a logon session having the specified ID, send the GET HTTP request to the /logonSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/logonSessions/{ID} |

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

In the response body, the REST API returns a representation of the /logonSessions/{ID} resource that contains the following parameters as well as links of resources available for the user account used for creating the logon session.

Response Body

| Element | Type | Description |
| UserName | String | User name of the account used for the logon session, for example: ENTERPRISE04\Administrator. |
| SessionId | String | Id of the logon session, for example: d7e68afd-cc15-4b1a-bd30-51eb309a1dab. |

Example

The example below returns a logon session created for Veeam Backup Enterprise Manager REST API. The logon session has ID 5496707f-c814-47ce-8d6d-110aa03cec03:

|  |
| --- |
| Request:  GET https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03">   <Links>     <Link Rel="Up" Type="EnterpriseManager" Href="https://localhost:9398/api/" />     <Link Rel="Down" Type="BackupServerReferenceList" Href="https://localhost:9398/api/backupServers" />     <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/managedServers" />     <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/jobs" />     <Link Rel="Down" Type="FailoverPlanReferenceList" Href="https://localhost:9398/api/failoverPlans" />     <Link Rel="Down" Type="HierarchyRootReferenceList" Href="https://localhost:9398/api/hierarchyRoots" />     <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/repositories" />     <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/backups" />     <Link Rel="Down" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints" />     <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/vmRestorePoints" />     <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/vAppRestorePoints" />     <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/replicas" />     <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/vmReplicaPoints" />     <Link Rel="Down" Type="CatalogVmReferenceList" Href="https://localhost:9398/api/catalog/vms" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/backupSessions" />     <Link Rel="Down" Type="RestoreSessionReferenceList" Href="https://localhost:9398/api/restoreSessions" />     <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/replicaSessions" />     <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupTaskSessions" />     <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaTaskSessions" />     <Link Rel="Down" Type="EnterpriseSecuritySettings" Href="https://localhost:9398/api/security" />     <Link Rel="Down" Type="WanAcceleratorReferenceList" Href="https://localhost:9398/api/wanAccelerators" />     <Link Rel="Down" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles" />     <Link Rel="Down" Type="TaskList" Href="https://localhost:9398/api/tasks" />     <Link Rel="Down" Type="QueryService" Href="https://localhost:9398/api/querySvc" />     <Link Rel="Down" Type="LookupService" Href="https://localhost:9398/api/lookupSvc" />     <Link Rel="Down" Type="Report" Href="https://localhost:9398/api/reports/summary" Name="Summary" />     <Link Rel="Down" Type="BackupServerList" Href="https://localhost:9398/api/backupServers?format=Entity" />     <Link Rel="Down" Type="ManagedServerList" Href="https://localhost:9398/api/managedServers?format=Entity" />     <Link Rel="Create" Href="https://localhost:9398/api/backupServers?action=create" />     <Link Rel="Down" Type="JobList" Href="https://localhost:9398/api/jobs?format=Entity" />     <Link Rel="Down" Type="FailoverPlanList" Href="https://localhost:9398/api/failoverPlans?format=Entity" />     <Link Rel="Down" Type="HierarchyRootList" Href="https://localhost:9398/api/hierarchyRoots?format=Entity" />     <Link Rel="Down" Type="RepositoryList" Href="https://localhost:9398/api/repositories?format=Entity" />     <Link Rel="Down" Type="BackupList" Href="https://localhost:9398/api/backups?format=Entity" />     <Link Rel="Down" Type="RestorePointList" Href="https://localhost:9398/api/restorePoints?format=Entity" />     <Link Rel="Down" Type="VmRestorePointList" Href="https://localhost:9398/api/vmRestorePoints?format=Entity" />     <Link Rel="Down" Type="VAppRestorePointList" Href="https://localhost:9398/api/vAppRestorePoints?format=Entity" />     <Link Rel="Down" Type="ReplicaList" Href="https://localhost:9398/api/replicas?format=Entity" />     <Link Rel="Down" Type="VmReplicaPointList" Href="https://localhost:9398/api/vmReplicaPoints?format=Entity" />     <Link Rel="Down" Type="CatalogVmList" Href="https://localhost:9398/api/catalog/vms?format=Entity" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://localhost:9398/api/backupSessions?format=Entity" />     <Link Rel="Down" Type="RestoreSessionList" Href="https://localhost:9398/api/restoreSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaJobSessionList" Href="https://localhost:9398/api/replicaSessions?format=Entity" />     <Link Rel="Down" Type="BackupTaskSessionList" Href="https://localhost:9398/api/backupTaskSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaTaskSessionList" Href="https://localhost:9398/api/replicaTaskSessions?format=Entity" />     <Link Rel="Down" Type="WanAcceleratorList" Href="https://localhost:9398/api/wanAccelerators?format=Entity" />     <Link Rel="Down" Type="VCloudService" Href="https://localhost:9398/api/vCloud" />     <Link Rel="Down" Type="BackupFileList" Href="https://localhost:9398/api/backupFiles?format=Entity" />     <Link Rel="Down" Type="CloudConnectService" Href="https://localhost:9398/api/cloud" />     <Link Rel="Delete" Href="https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03" />   </Links>   <UserName>SRV13\Administrator</UserName>   <SessionId>5496707f-c814-47ce-8d6d-110aa03cec03</SessionId> </LogonSession> |

Page updated 2026-07-29

