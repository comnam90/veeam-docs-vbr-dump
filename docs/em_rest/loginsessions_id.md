---
title: "/logonSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/loginsessions_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /logonSessions/{ID}


Represents a currently existing logon session having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/logonsessions/{ID} |

Related Resources

[/logonSessions](loginsessions.md)

Methods

The following methods are supported for the /logonSessions/{ID} resource:

* [GET /logonSessions/{ID}](get_loginsessions_id.md)
* [DELETE /logonSessions/{ID}](delete_loginsessions_id.md)

Resource Representation

The /logonSessions/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03">   <Links>     <Link Rel="Up" Type="EnterpriseManager" Href="https://localhost:9398/api/" />     <Link Rel="Down" Type="BackupServerReferenceList" Href="https://localhost:9398/api/backupServers" />     <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/managedServers" />     <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/jobs" />     <Link Rel="Down" Type="FailoverPlanReferenceList" Href="https://localhost:9398/api/failoverPlans" />     <Link Rel="Down" Type="HierarchyRootReferenceList" Href="https://localhost:9398/api/hierarchyRoots" />     <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/repositories" />     <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/backups" />     <Link Rel="Down" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints" />     <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/vmRestorePoints" />     <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/vAppRestorePoints" />     <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/replicas" />     <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/vmReplicaPoints" />     <Link Rel="Down" Type="CatalogVmReferenceList" Href="https://localhost:9398/api/catalog/vms" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/backupSessions" />     <Link Rel="Down" Type="RestoreSessionReferenceList" Href="https://localhost:9398/api/restoreSessions" />     <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/replicaSessions" />     <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupTaskSessions" />     <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaTaskSessions" />     <Link Rel="Down" Type="EnterpriseSecuritySettings" Href="https://localhost:9398/api/security" />     <Link Rel="Down" Type="WanAcceleratorReferenceList" Href="https://localhost:9398/api/wanAccelerators" />     <Link Rel="Down" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles" />     <Link Rel="Down" Type="TaskList" Href="https://localhost:9398/api/tasks" />     <Link Rel="Down" Type="QueryService" Href="https://localhost:9398/api/querySvc" />     <Link Rel="Down" Type="LookupService" Href="https://localhost:9398/api/lookupSvc" />     <Link Rel="Down" Type="Report" Href="https://localhost:9398/api/reports/summary" Name="Summary" />     <Link Rel="Down" Type="BackupServerList" Href="https://localhost:9398/api/backupServers?format=Entity" />     <Link Rel="Down" Type="ManagedServerList" Href="https://localhost:9398/api/managedServers?format=Entity" />     <Link Rel="Create" Href="https://localhost:9398/api/backupServers?action=create" />     <Link Rel="Down" Type="JobList" Href="https://localhost:9398/api/jobs?format=Entity" />     <Link Rel="Down" Type="FailoverPlanList" Href="https://localhost:9398/api/failoverPlans?format=Entity" />     <Link Rel="Down" Type="HierarchyRootList" Href="https://localhost:9398/api/hierarchyRoots?format=Entity" />     <Link Rel="Down" Type="RepositoryList" Href="https://localhost:9398/api/repositories?format=Entity" />     <Link Rel="Down" Type="BackupList" Href="https://localhost:9398/api/backups?format=Entity" />     <Link Rel="Down" Type="RestorePointList" Href="https://localhost:9398/api/restorePoints?format=Entity" />     <Link Rel="Down" Type="VmRestorePointList" Href="https://localhost:9398/api/vmRestorePoints?format=Entity" />     <Link Rel="Down" Type="VAppRestorePointList" Href="https://localhost:9398/api/vAppRestorePoints?format=Entity" />     <Link Rel="Down" Type="ReplicaList" Href="https://localhost:9398/api/replicas?format=Entity" />     <Link Rel="Down" Type="VmReplicaPointList" Href="https://localhost:9398/api/vmReplicaPoints?format=Entity" />     <Link Rel="Down" Type="CatalogVmList" Href="https://localhost:9398/api/catalog/vms?format=Entity" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://localhost:9398/api/backupSessions?format=Entity" />     <Link Rel="Down" Type="RestoreSessionList" Href="https://localhost:9398/api/restoreSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaJobSessionList" Href="https://localhost:9398/api/replicaSessions?format=Entity" />     <Link Rel="Down" Type="BackupTaskSessionList" Href="https://localhost:9398/api/backupTaskSessions?format=Entity" />     <Link Rel="Down" Type="ReplicaTaskSessionList" Href="https://localhost:9398/api/replicaTaskSessions?format=Entity" />     <Link Rel="Down" Type="WanAcceleratorList" Href="https://localhost:9398/api/wanAccelerators?format=Entity" />     <Link Rel="Down" Type="VCloudService" Href="https://localhost:9398/api/vCloud" />     <Link Rel="Down" Type="BackupFileList" Href="https://localhost:9398/api/backupFiles?format=Entity" />     <Link Rel="Down" Type="CloudConnectService" Href="https://localhost:9398/api/cloud" />     <Link Rel="Delete" Href="https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03" />   </Links>   <UserName>SRV13\Administrator</UserName>   <SessionId>5496707f-c814-47ce-8d6d-110aa03cec03</SessionId> </LogonSession> |

Page updated 2026-07-29

