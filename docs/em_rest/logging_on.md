---
title: "logging_on"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/logging_on.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Before you can start working with Veeam Backup Enterprise Manager REST API resources, you must log on to Veeam Backup Enterprise Manager and create a new logon session.

1. When you access the Veeam Backup Enterprise Manager REST API by its base URL, Veeam Backup Enterprise Manager returns a representation with a link to a list of existing sessions and links to creating a new logon session. The SupportedVersion sections in the representation indicate versions of Veeam Backup Enterprise Manager REST API. You can create a new logon session to work with resources that are supported in the latest or the specified version of REST API.

To work with all Veeam Backup Enterprise Manager REST API resources available in the current version of Veeam Backup & Replication and to access a complete set of actions that can be performed with those resources, create a new logon session using the link to the latest version of the /sessionMngr resource. For example, to work with REST API resources supported in Veeam Backup & Replication 13, create a new logon session using one of the following links:

* https://localhost:9398/api/sessionMngr/?v=latest
* https://localhost:9398/api/sessionMngr/?v=v1\_6

If a previous version of Veeam Backup & Replication is installed on your backup server, you need to create a new logon session with the link to the REST API version that matches the version of Veeam Backup & Replication. For details, see [Versioning](em_web_api_versions.md).

|  |
| --- |
| Request:  GET https://localhost:9398/api/    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

1. As there are no existing logon sessions, you need to create a new one. A new logon session is created by sending the POST HTTP request to the /sessionMngr/ resource. In the header of the request, provide user credentials of the account you plan to use for the current logon session. To make up the credentials string:

1. Construct a string in the username:password format.
2. Encode the string with base64 encoding.
3. Add the Authorization header to the POST HTTP request. In the value of the header, specify Basic <encoded\_string>:

|  |
| --- |
| Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ= |

1. Send the composed POST HTTP request to the /sessionMngr/ resource. Veeam Backup Enterprise Manager will return a list of resources with which you can work using Veeam Backup Enterprise Manager REST API. In the UserName element, Veeam Backup Enterprise Manager will return a name of the user who is currently logged on. In the header of the response, Veeam Backup Enterprise Manager will supply a newly generated authorization token for the created logon session:

|  |
| --- |
| Request:  POST https://localhost:9398/api/sessionMngr/?v=v1\_7    Request Header:  Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=    Response:  201 Created    Response Header:  X-RestSvcSessionId: O9Msj3rq7EGUhtSMBQx+mw==    Response Body:  <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://srv12.tech.local:9398/api/logonSessions/15a3fc97-0325-4119-b789-5c0367c6c565">   <Links>     <Link Rel="Up" Type="EnterpriseManager" Href="https://srv12.tech.local:9398/api/" />     <Link Rel="Down" Type="BackupServerReferenceList" Href="https://srv12.tech.local:9398/api/backupServers" />     <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://srv12.tech.local:9398/api/managedServers" />     <Link Rel="Down" Type="JobReferenceList" Href="https://srv12.tech.local:9398/api/jobs" />     <Link Rel="Down" Type="FailoverPlanReferenceList" Href="https://srv12.tech.local:9398/api/failoverPlans" />     <Link Rel="Down" Type="HierarchyRootReferenceList" Href="https://srv12.tech.local:9398/api/hierarchyRoots" />     <Link Rel="Down" Type="RepositoryReferenceList" Href="https://srv12.tech.local:9398/api/repositories" />     <Link Rel="Down" Type="BackupReferenceList" Href="https://srv12.tech.local:9398/api/backups" />     <Link Rel="Down" Type="RestorePointReferenceList" Href="https://srv12.tech.local:9398/api/restorePoints" />     <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://srv12.tech.local:9398/api/vmRestorePoints" />     <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://srv12.tech.local:9398/api/vAppRestorePoints" />     <Link Rel="Down" Type="ReplicaReferenceList" Href="https://srv12.tech.local:9398/api/replicas" />     <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://srv12.tech.local:9398/api/vmReplicaPoints" />     <Link Rel="Down" Type="CatalogVmReferenceList" Href="https://srv12.tech.local:9398/api/catalog/vms" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions" />     <Link Rel="Down" Type="RestoreSessionReferenceList" Href="https://srv12.tech.local:9398/api/restoreSessions" />     <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/replicaSessions" />     <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupTaskSessions" />     <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/replicaTaskSessions" />     <Link Rel="Down" Type="EnterpriseSecuritySettings" Href="https://srv12.tech.local:9398/api/security" />     <Link Rel="Down" Type="WanAcceleratorReferenceList" Href="https://srv12.tech.local:9398/api/wanAccelerators" />     <Link Rel="Down" Type="BackupFileReferenceList" Href="https://srv12.tech.local:9398/api/backupFiles" />     <Link Rel="Down" Type="ExternalRepositoryReferenceList" Href="https://srv12.tech.local:9398/api/externalRepositories" />     <Link Rel="Down" Type="TaskList" Href="https://srv12.tech.local:9398/api/tasks" />     <Link Rel="Down" Type="QueryService" Href="https://srv12.tech.local:9398/api/querySvc" />     <Link Rel="Down" Type="LookupService" Href="https://srv12.tech.local:9398/api/lookupSvc" />     <Link Rel="Down" Type="Report" Href="https://srv12.tech.local:9398/api/reports/summary" Name="Summary" />     <Link Rel="Down" Type="BackupServerList" Href="https://srv12.tech.local:9398/api/backupServers?format=Entity" />     <Link Rel="Down" Type="ManagedServerList" Href="https://srv12.tech.local:9398/api/managedServers?format=Entity" />     <Link Rel="Create" Href="https://srv12.tech.local:9398/api/backupServers?action=create" />     <Link Rel="Down" Type="JobList" Href="https://srv12.tech.local:9398/api/jobs?format=Entity" />     <Link Rel="Down" Type="FailoverPlanList" Href="https://srv12.tech.local:9398/api/failoverPlans?format=Entity" />     <Link Rel="Down" Type="HierarchyRootList" Href="https://srv12.tech.local:9398/api/hierarchyRoots?format=Entity" />     <Link Rel="Down" Type="RepositoryList" Href="https://srv12.tech.local:9398/api/repositories?format=Entity" />     <Link Rel="Down" Type="BackupList" Href="https://srv12.tech.local:9398/api/backups?format=Entity" />     <Link Rel="Down" Type="RestorePointList" Href="https://srv12.tech.local:9398/api/restorePoints?format=Entity" />     <Link Rel="Down" Type="VmRestorePointList" Href="https://srv12.tech.local:9398/api/vmRestorePoints?format=Entity" />     <Link Rel="Down" Type="VAppRestorePointList" Href="https://srv12.tech.local:9398/api/vAppRestorePoints?format=Entity" />     <Link Rel="Down" Type="ReplicaList" Href="https://srv12.tech.local:9398/api/replicas?format=Entity" />     <Link Rel="Down" Type="VmReplicaPointList" Href="https://srv12.tech.local:9398/api/vmReplicaPoints?format=Entity" />     <Link Rel="Down" Type="CatalogVmList" Href="https://srv12.tech.local:9398/api/catalog/vms?format=Entity" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://srv12.tech.local:9398/api/backupSessions?format=Entity" />     <Link Rel="Down" Type="RestoreSessionList" Href="https://srv12.tech.local:9398/api/restoreSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaJobSessionList" Href="https://srv12.tech.local:9398/api/replicaSessions?format=Entity" />     <Link Rel="Down" Type="BackupTaskSessionList" Href="https://srv12.tech.local:9398/api/backupTaskSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaTaskSessionList" Href="https://srv12.tech.local:9398/api/replicaTaskSessions?format=Entity" />     <Link Rel="Down" Type="WanAcceleratorList" Href="https://srv12.tech.local:9398/api/wanAccelerators?format=Entity" />     <Link Rel="Down" Type="VCloudService" Href="https://srv12.tech.local:9398/api/vCloud" />     <Link Rel="Down" Type="BackupFileList" Href="https://srv12.tech.local:9398/api/backupFiles?format=Entity" />     <Link Rel="Down" Type="AgentsService" Href="https://srv12.tech.local:9398/api/agents" />     <Link Rel="Down" Type="VSphereSelfService" Href="https://srv12.tech.local:9398/api/selfService/vSphere" />     <Link Rel="Down" Type="ExternalRepositoryList" Href="https://srv12.tech.local:9398/api/externalRepositories?format=Entity" />     <Link Rel="Down" Type="NasService" Href="https://srv12.tech.local:9398/api/nas" />     <Link Rel="Delete" Href="https://srv12.tech.local:9398/api/logonSessions/15a3fc97-0325-4119-b789-5c0367c6c565" />   </Links>   <UserName>SRV12\Administrator</UserName>   <SessionId>15a3fc97-0325-4119-b789-5c0367c6c565</SessionId> </LogonSession> |

1. You must copy the obtained X-RestSvcSessionId header and send it in the header of all subsequent requests to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| To create a new logon session for a tenant, you need to provide tenant credentials in the body of the POST HTTP request to the /sessionMngr/ resource. For details, see [Tenant Logon Session](cloud_connect_tenant_credentials.md). |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
