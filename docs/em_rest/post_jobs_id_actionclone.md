---
title: "post_jobs_id_actionclone"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_jobs_id_actionclone.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a copy of the job having the specified ID. The cloned job is registered on the same backup server where the initial job is created.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To clone a job, send the POST HTTP request to the /jobs/{ID}?action=clone URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/jobs/{ID}?action=clone |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the cloned job. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

The request body differs depending on the type of the cloned job:

* [Backup job](#backup)
* [Replication job](#replica)
* [Backup copy job](#copy)
* [Immediate backup copy job](#immediate)

Backup Job Clone Options

For a backup job, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| JobName | String | Name of the new cloned job. The name must be up to 50 characters long. | Yes | 1/1 |
| FolderName | String | Name of the backup file that will be created by the cloned job. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository in which the backup file will be created. | No | 1/1 |
| Description | String | Description for the cloned job. | Yes | 0/1 |

For example:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

Replication Job Clone Options

For a replication job, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| JobName | String | Name of the new cloned job. The name must be up to 50 characters long. | Yes | 1/1 |
| VmSuffix | String | Suffix for the name of a VM replica created by the cloned job. | Yes | 1/1 |
| Description | String | Description for the cloned job. | Yes | 0/1 |

For example:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <JobCloneSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <ReplicaJobCloneInfo>     <JobName>Cloned job (2/11/2020 6:13:50 PM)</JobName>     <VmSuffix>\_replica</VmSuffix>     <Description>This job was created by cloning Appserver Replication job</Description>   </ReplicaJobCloneInfo> </JobCloneSpec> |

Backup Copy Job Clone Options

For a backup copy job, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| JobName | String | Name of the new cloned job. The name must be up to 50 characters long. | Yes | 1/1 |
| JobFileName | String | Name of the backup file that will be created by the cloned job. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository in which the backup file will be created. | No | 1/1 |
| Description | String | Description for the cloned job. | Yes | 0/1 |

For example:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <JobCloneSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <BackupCopyJobCloneInfo>     <JobName>Cloned job (2/11/2020 6:15:44 PM)</JobName>     <JobFileName>Cloned job \_2\_11\_2020 6\_15\_44 PM\_</JobFileName>     <RepositoryUid>urn:veeam:Repository:8a511e84-067a-4f0c-a30d-ad79092691be</RepositoryUid>     <Description>This job was created by cloning CRM Backup Copy job</Description>   </BackupCopyJobCloneInfo> </JobCloneSpec> |

Immediate Backup Copy Job Clone Options

For an immediate backup copy job, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| JobName | String | Name of the new cloned job. The name must be up to 50 characters long. | Yes | 1/1 |
| JobFileName | String | Name of the backup file that will be created by the cloned job. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository in which the backup file will be created. | No | 1/1 |
| Description | String | Description for the cloned job. | Yes | 0/1 |

For example:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <JobCloneSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <ImmediateBackupCopyJobCloneInfo>     <JobName>Cloned job (2/11/2020 6:17:41 PM)</JobName>     <Description>This job was created by cloning Backup Copy job</Description>     <RepositoryUid>urn:veeam:Repository:cf99cfbb-e097-432c-bafb-6558d3957f5b</RepositoryUid>     <JobFileName>Cloned job \_2\_11\_2020 6\_17\_41 PM\_</JobFileName>   </ImmediateBackupCopyJobCloneInfo> </JobCloneSpec> |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

Example

The example below clones a job having ID 78c3919c-54d7-43fe-b047-485d3566f11f.

|  |
| --- |
| Request:  POST https://localhost:9398/api/jobs/78c3919c-54d7-43fe-b047-485d3566f11f?action=clone    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <JobCloneSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <BackupJobCloneInfo>     <JobName>Oracle Backup 01</JobName>     <FolderName>Oracle Backup 01</FolderName>     <RepositoryUid>urn:veeam:Repository:cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55</RepositoryUid>     <Description>Cloned Oracle backup job</Description>   </BackupJobCloneInfo> </JobCloneSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CloneJob</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="Job" Href="https://localhost:9398/api/jobs/1ef18e6a-531a-4dbd-bb96-827478a25965?format=Entity" Name="Oracle Backup cloned at 10/18/2014 6:13:11 AM" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CloneJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
