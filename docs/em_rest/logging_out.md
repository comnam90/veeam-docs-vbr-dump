---
title: "Step 4. Perform Logout"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/logging_out.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Perform Logout


To finish working with Veeam Backup Enterprise Manager REST API and log out:

1. Send the GET HTTP request to the /logonSessions resource to get a list of existing logon sessions:

|  |
| --- |
| Request:  GET https://localhost:9398/api/logonSessions  Response:  200 OK  Response Body:  <LogonSessions xmlns="http://www.veeam.com/ent/v1.0">   <LogonSession Type="LogonSession" Href="https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57">     <Links>       <Link Rel="Up" Type="EnterpriseManager" Href="https://localhost:9398/api/" />       <Link Rel="Down" Type="BackupServerReferenceList" Href="https://localhost:9398/api/backupServers" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/managedServers" />       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/jobs" />       <Link Rel="Down" Type="FailoverPlanReferenceList" Href="https://localhost:9398/api/failoverPlans" />       <Link Rel="Down" Type="HierarchyRootReferenceList" Href="https://localhost:9398/api/hierarchyRoots" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/repositories" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/backups" />       <Link Rel="Down" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/vAppRestorePoints" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/replicas" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/vmReplicaPoints" />       <Link Rel="Down" Type="CatalogVmReferenceList" Href="https://localhost:9398/api/catalog/vms" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/backupSessions" />       <Link Rel="Down" Type="RestoreSessionReferenceList" Href="https://localhost:9398/api/restoreSessions" />       <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/replicaSessions" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupTaskSessions" />       <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaTaskSessions" />       <Link Rel="Down" Type="EnterpriseSecuritySettings" Href="https://localhost:9398/api/security" />       <Link Rel="Down" Type="WanAcceleratorReferenceList" Href="https://localhost:9398/api/wanAccelerators" />       <Link Rel="Down" Type="TaskList" Href="https://localhost:9398/api/tasks" />       <Link Rel="Down" Type="QueryService" Href="https://localhost:9398/api/querySvc" />       <Link Rel="Down" Type="LookupService" Href="https://localhost:9398/api/lookupSvc" />       <Link Rel="Down" Type="Report" Href="https://localhost:9398/api/reports/summary" Name="Summary" />       <Link Rel="Down" Type="BackupServerList" Href="https://localhost:9398/api/backupServers?format=Entity" />       <Link Rel="Down" Type="ManagedServerList" Href="https://localhost:9398/api/managedServers?format=Entity" />       <Link Rel="Create" Href="https://localhost:9398/api/backupServers?action=create" />       <Link Rel="Down" Type="JobList" Href="https://localhost:9398/api/jobs?format=Entity" />       <Link Rel="Down" Type="FailoverPlanList" Href="https://localhost:9398/api/failoverPlans?format=Entity" />       <Link Rel="Down" Type="HierarchyRootList" Href="https://localhost:9398/api/hierarchyRoots?format=Entity" />       <Link Rel="Down" Type="RepositoryList" Href="https://localhost:9398/api/repositories?format=Entity" />       <Link Rel="Down" Type="BackupList" Href="https://localhost:9398/api/backups?format=Entity" />       <Link Rel="Down" Type="RestorePointList" Href="https://localhost:9398/api/restorePoints?format=Entity" />       <Link Rel="Down" Type="VmRestorePointList" Href="https://localhost:9398/api/vmRestorePoints?format=Entity" />       <Link Rel="Down" Type="VAppRestorePointList" Href="https://localhost:9398/api/vAppRestorePoints?format=Entity" />       <Link Rel="Down" Type="ReplicaList" Href="https://localhost:9398/api/replicas?format=Entity" />       <Link Rel="Down" Type="VmReplicaPointList" Href="https://localhost:9398/api/vmReplicaPoints?format=Entity" />       <Link Rel="Down" Type="CatalogVmList" Href="https://localhost:9398/api/catalog/vms?format=Entity" />       <Link Rel="Down" Type="BackupJobSessionList" Href="https://localhost:9398/api/backupSessions?format=Entity" />       <Link Rel="Down" Type="RestoreSessionList" Href="https://localhost:9398/api/restoreSessions?format=Entity" />       <Link Rel="Down" Type="ReplicaJobSessionList" Href="https://localhost:9398/api/replicaSessions?format=Entity" />       <Link Rel="Down" Type="BackupTaskSessionList" Href="https://localhost:9398/api/backupTaskSessions?format=Entity" />       <Link Rel="Down" Type="ReplicaTaskSessionList" Href="https://localhost:9398/api/replicaTaskSessions?format=Entity" />       <Link Rel="Down" Type="WanAcceleratorList" Href="https://localhost:9398/api/wanAccelerators?format=Entity" />       <Link Rel="Down" Type="CloudConnectService" Href="https://localhost:9398/api/cloud" />       <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57" />     </Links>     <UserName>SRV36\Administrator</UserName>     <SessionId>695f7cda-e4a6-4d9c-9603-8a6b05693c57</SessionId>   </LogonSession> </LogonSessions> |

1. Examine the representation of the logon session and find a link to logon session deletion:

|  |
| --- |
| <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57" |

1. Send the DELETE HTTP request to the obtained link:

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57  Response:  204 No Content |

1. If you are using Veeam Backup Enterprise Manager Web Client, close the browser window.

The logon session will be deleted.

Page updated 2026-07-29

