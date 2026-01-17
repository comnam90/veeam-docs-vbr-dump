---
title: "Performing 1-Click Restore"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/scenario_1_click_restore.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Performing 1-Click Restore


Using Veeam Backup Enterprise Manager REST API, you can restore a VM guest OS file or folder from the backup to its initial location on the VM guest OS.

Prerequisites

* Make sure you are logged on to Veeam Backup Enterprise Manager under the user account to which the Portal Administrator, Portal User or Restore Operator role is assigned.
* If you are logged on using the account to which the Portal User or Restore Operator role is assigned, make sure that your restore scope permits you to restore guest OS files from the necessary VM.

Procedure

1. After you [access](accessing_em_web_api.md) Veeam Backup Enterprise Manager [REST API](accessing_em_web_api.md) and [create a new logon session](logging_on.md), examine the representation of the logon session that the server has returned:

|  |
| --- |
| Request:  POST https://localhost:9398/api/sessionMngr/?v=v1\_7    Request Header:  Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=    Response:  201 Created    Response Header:  X-RestSvcSessionId: NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response Body:    <LogonSessions xmlns="http://www.veeam.com/ent/v1.0"> |

1. Find the link for the /catalog/vms resource collection:

|  |
| --- |
| <Link Rel="Down" Type="CatalogVmReferenceList" Href="https://localhost:9398/api/catalog/vms" /> |

1. From the link, retrieve the URL for the /catalog/vms collection. The URL is specified in the Href element. Send the GET HTTP request to the retrieved URL. The server will return a representation of all VMs whose guest OS files have been indexed during backup.

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CatalogVmReference" Href="https://localhost:9398/api/catalog/vms/fileserver01" Name="fileserver01" UID="urn:veeam:CatalogVm:fileserver01">     <Links>       <Link Rel="Alternate" Href="https://localhost:9398/api/catalog/vms/fileserver01?format=Entity" />       <Link Rel="Down" Type="CatalogVmRestorePointReferenceList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints" />     </Links>   </Ref>   ... </EntityReferences> |

1. Examine the received resource representation and find a link to the entity of the necessary VM. The Rel attribute in the link is set to Alternate:

|  |
| --- |
| <Link Rel="Alternate" Href="https://localhost:9398/api/catalog/vms/fileserver01?format=Entity" /> |

1. Retrieve the URL for the VM resource and send the GET HTTP request to the retrieved URL. The server will return a resource representation of the VM:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CatalogVm xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVm" Href="https://localhost:9398/api/catalog/vms/fileserver01?format=Entity" Name="fileserver01" UID="urn:veeam:CatalogVm:fileserver01" VmDisplayName="fileserver01">   <Links>     <Link Rel="Alternate" Type="CatalogVmReference" Href="https://localhost:9398/api/catalog/vms/fileserver01" Name="fileserver01" />     <Link Rel="Down" Type="CatalogVmRestorePointReferenceList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints" />   </Links> </CatalogVm> |

1. Examine the received resource representation and find a link to the list of restore point for the given VM. Retrieve the URL for the VM restore points collection and send the GET HTTP request to the retrieved URL. The server will return a resource representation of the restore points collection:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462" Name="8/26/2016 7:59:00 AM" UID="urn:veeam:CatalogVmRestorePoint:d2bfab92-7286-454e-ada5-55dd8146d462">     <Links>       <Link Rel="Up" Href="https://localhost:9398/api/catalog/vms/fileserver01" />       <Link Rel="Alternate" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?format=Entity" />     </Links>   </Ref> </EntityReferences> |

1. Examine the received resource representation and find a link to the entity resource representation for the necessary VM restore point. Send the GET HTTP request to the retrieved URL. The server will return a resource representation of the selected restore point:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CatalogVmRestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVmRestorePoint" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?format=Entity" Name="fileserver01" UID="urn:veeam:CatalogVmRestorePoint:d2bfab92-7286-454e-ada5-55dd8146d462">   <Links>     <Link Rel="Alternate" Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462" Name="fileserver01" />     <Link Rel="Up" Type="CatalogVm" Href="https://localhost:9398/api/catalog/vms/fileserver01?format=Entity" Name="fileserver01" />     <Link Rel="Browse" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?action=browse" />     <Link Rel="Related" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?format=Entity" Name="fileserver01" />   </Links>   <BackupDateUTC>2017-01-06T07:59:00Z</BackupDateUTC> </CatalogVmRestorePoint> |

1. Find a link to the browse action and send the POST HTTP request to the URL in the link. In response, Veeam Backup Enterprise Manager creates a new task and returns the HTTP/1.1 202 ACCEPTED status to the client. In the response body, Veeam Backup Enterprise Manager returns a resource representation of the task.

|  |
| --- |
| Request:  POST https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462?action=browse    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Created    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>BrowseVM</Operation>   <Result Success="true" /> </Task> |

1. In the resource representation of the task, the server also returns a link to the VM guest OS file system. Send the GET HTTP request to the guest OS file system resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <FileSystemEntry xmlns="http://www.veeam.com/ent/v1.0">   <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/">     <Links>       <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/?action=listAll" />       <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/?action=listFiles&pageSize=10&page=1" />       <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/?action=listDirs&pageSize=10&page=1" />     </Links>   </DirectoryEntry> </FileSystemEntry> |

1. Construct the URL for the resource of the directory in which the file you plan to restore resides. The URL is constructed by the following pattern: /catalog/vms/{ID}/vmRestorePoints/{ID}/guestfs/{filepath}, where {filepath} is the path to the directory on the VM guest OS.

Send the GET HTTP request to the constructed URL:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK |

1. The resource representation of the directory contains a set of links that allow you to perform the following actions:

* Display all entries, both files and subdirectories, in the directory
* Display all files in the directory
* Display all subdirectories in the directory

 To get a list of all files, send the GET HTTP request to the /catalog/vms/{ID}/vmRestorePoints/{ID}/guestfs/(filepath}?action=listAll URL:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents?action=listAll    Request Header:  X-RestSvcSessionId:  NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <FileSystemEntries xmlns="http://www.veeam.com/ent/v1.0">   <Links>     <Link Rel="Up" Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents" />   </Links>   <Files>     <FileEntry Type="FileEntry" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents/Invoice1.docx">       <Links>         <Link Rel="Restore" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents/Invoice1.docx?action=restore" />       </Links>       <Path>C:/Documents/Invoice1.docx</Path>       <Name>Invoice1.docx</Name>       <Size>16896000</Size>       <Owner>Administrators</Owner>       <ModifiedDateUTC>2013-08-14T17:13:36Z</ModifiedDateUTC>     </FileEntry>     <FileEntry Type="FileEntry" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents/Invoice2.docx">       <Links>         <Link Rel="Restore" Href="https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents/Invoice2.docx?action=restore" />       </Links>       <Path>C:/Documents/Invoice2.docx</Path>       <Name>Invoice2.docx</Name>       <Size>16896000</Size>       <Owner>Administrators</Owner>       <ModifiedDateUTC>2013-08-16T17:04:41Z</ModifiedDateUTC>     </FileEntry>     ...   </Files>   <Directories /> </FileSystemEntries> |

1. Find a link to the restore action for the necessary file in the directory and send the POST HTTP request to the URL in the link. In response, Veeam Backup Enterprise Manager creates a new task and returns the HTTP/1.1 202 ACCEPTED status to the client. In the response body, Veeam Backup Enterprise Manager returns a resource representation of the task.

|  |
| --- |
| Request:  POST https://localhost:9398/api/catalog/vms/fileserver01/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462/guestfs/C:/Documents/Invoice1.docx?action=restore    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Created    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>RestoreFile</Operation> </Task> |

1. Send the GET HTTP request to the task URL to learn about the task completion.

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity" Name="Restore job session" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>RestoreFile</Operation>   <Result Success="true">     <Message>Restore operations started successfully.</Message>   </Result> </Task> |

1. In the resource representation of the task, the server also returns a link to the restore session. Send the GET HTTP request to the restore session to monitor the restore session progress:

|  |
| --- |
| Request:  GET https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <RestoreSession xmlns="http://www.veeam.com/ent/v1.0" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity" Name="FLR\_[fileserver01]@2017-01-12 16:54:40" UID="urn:veeam:RestoreSession:8f20b44a-b96f-47c6-9a17-ba9d1c17a342" VmDisplayName="fileserver01">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/be21c981-7353-4896-8b69-0bf300c05337" Name="172.17.53.1" />     <Link Rel="Alternate" Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342" Name="FLR\_[fileserver01]@2017-01-12 16:54:40" />     <Link Rel="Related" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462" Name="filesever01@2017-01-06 07:59:00" />   </Links>   <JobType>FileLevelRestore</JobType>   <CreationTimeUTC>2017-01-12T16:54:40Z</CreationTimeUTC>   <EndTimeUTC>2017-01-12T16:56:28.7Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>100</Progress> </RestoreSession> |

Result

The file is restored to its initial location on the VM guest OS.


