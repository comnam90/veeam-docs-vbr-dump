---
title: "Performing Entire VM Restore"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/scenario_vm_restore.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Performing Entire VM Restore


Using Veeam Backup Enterprise Manager REST API, you can perform the entire VM restore operation.

Prerequisites

* Make sure you are logged on to Veeam Backup Enterprise Manager under the user account to which the Portal Administrator, Portal User or Restore Operator role is assigned.
* If you are logged on using the account to which the Portal User or Restore Operator role is assigned, make sure that your restore scope permits you to restore the necessary VM.

Procedure

1. After you [access](accessing_em_web_api.md) Veeam Backup Enterprise Manager [REST API](accessing_em_web_api.md) and [create a new logon session](logging_on.md), examine the representation of the logon session that the server has returned:

|  |
| --- |
| Request:  POST https://localhost:9398/api/sessionMngr/?v=v1\_6    Request Header:  Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=    Response:  201 Created    Response Header:  X-RestSvcSessionId: NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response Body:  <LogonSessions xmlns="http://www.veeam.com/ent/v1.0"> |

1. Find the link for the /vmRestorePoints resource collection:

|  |
| --- |
| <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/vmRestorePoints" /> |

1. From the link, retrieve the URL for the /vmRestorePoints collection. The URL is specified in the Href element. Send the GET HTTP request to the retrieved URL. The server will return a representation of all VM restore points that have been created by backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmRestorePoints    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/7e26714d-4d44-4bf1-af0e-158e9f7f5f66" Name="sql01-hv@2013-08-21 10:46:42" UID="urn:veeam:VmRestorePoint:7e26714d-4d44-4bf1-af0e-158e9f7f5f66">     <Links>       <Link Rel="Up" Type="localhostReference" Href="https://localhost:9398/api/localhosts/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/fcf92506-ee3e-4612-bfb5-68ab2d472532" Name="Aug 21 2013 10:46AM" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/7e26714d-4d44-4bf1-af0e-158e9f7f5f66?format=Entity" Name="sql01-hv@2013-08-21 10:46:42" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415" Name="sql01-hv@2013-08-21 10:44:36" UID="urn:veeam:VmRestorePoint:a712861b-0dd3-405b-8b75-2fbee55fb415">     <Links>       <Link Rel="Up" Type="localhostReference" Href="https://localhost:9398/api/localhosts/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/6f30b893-7103-4925-bef0-48ca943ae6b6" Name="Aug 21 2013 10:44AM" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?format=Entity" Name="sql01-hv@2013-08-21 10:44:36" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5c0d5a40-714c-457c-a005-3ccca1730468" Name="hp\_vm1@2013-08-21 13:32:48" UID="urn:veeam:VmRestorePoint:5c0d5a40-714c-457c-a005-3ccca1730468">     <Links>       <Link Rel="Up" Type="localhostReference" Href="https://localhost:9398/api/localhosts/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/93731898-da96-4830-b74c-d632a8590746" Name="Aug 21 2013  1:32PM" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/5c0d5a40-714c-457c-a005-3ccca1730468?format=Entity" Name="hp\_vm1@2013-08-21 13:32:48" />     </Links>   </Ref>  ... </EntityReferences> |

1. Examine the received resource representation and find a link to the entity of the necessary restore point. The Rel attribute in the link is set to Alternate:

|  |
| --- |
| <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?format=Entity" Name="sql01-hv@2013-08-21 10:44:36" /> </Links> |

1. Retrieve the URL for the VM restore point and send the GET HTTP request to the retrieved URL. The server will return a resource representation of the VM restore point:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VmRestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?format=Entity" Name="sql01-hv@2013-08-21 10:44:36" UID="urn:veeam:VmRestorePoint:a712861b-0dd3-405b-8b75-2fbee55fb415" VmDisplayName="sql01-hv">   <Links>     <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?action=restore" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />     <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/6f30b893-7103-4925-bef0-48ca943ae6b6" Name="Aug 21 2013 10:44AM" />     <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415" Name="sql01-hv@2013-08-21 10:44:36" />     <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415/mounts" />     <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415/mounts" />   </Links>   <CreationTimeUTC>2013-08-21T10:44:36Z</CreationTimeUTC>   <Algorithm>Full</Algorithm>   <PointType>Full</PointType> </VmRestorePoint> |

1. Find a link to the entire VM restore action and send the POST HTTP request to the URL in the link. The VM restore process is started asynchronously: Veeam Backup Enterprise Manager creates a new task for the VM restore and returns the HTTP/1.1 202 ACCEPTED status to the client. In the response body, Veeam Backup Enterprise Manager returns a resource representation of the task.

|  |
| --- |
| Request:  POST https://localhost:9398/api/vmRestorePoints/a712861b-0dd3-405b-8b75-2fbee55fb415?action=restore    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Created    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>StartVMRestore</Operation> </Task> |

1. Every task has its own ID. In the given example, the task ID is task-1. To track the task performance and check the task result, send the GET HTTP request to the task resource. The server will return a resource representation of the task describing the task status and result:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/b67a3603-81f4-46af-be68-9f2c2307465c?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartVMRestore</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

1. In the resource representation of the task, the server also returns a link to the restore session resource created once the restore process is started. You can check the restore session details by sending the GET HTTP request to the restore session resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/restoreSessions/b67a3603-81f4-46af-be68-9f2c2307465c?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <RestoreSession xmlns="http://www.veeam.com/ent/v1.0" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/b67a3603-81f4-46af-be68-9f2c2307465c?format=Entity" Name="sql01-hv@2013-08-26 08:31:22" UID="urn:veeam:RestoreSession:b67a3603-81f4-46af-be68-9f2c2307465c" VmDisplayName="sql01-hv">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />     <Link Rel="Alternate" Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/b67a3603-81f4-46af-be68-9f2c2307465c" Name="sql01-hv@2013-08-26 08:31:22" />   </Links>   <JobType>RestoreVm</JobType>   <CreationTimeUTC>2013-08-26T08:31:22Z</CreationTimeUTC>   <EndTimeUTC>2013-08-26T08:31:34Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result> </RestoreSession> |

Result

The VM is restored from the backup to its initial location.


