---
title: "post_cloudfailoverplans_id_test"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cloudfailoverplans_id_test.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Tests a cloud failover plan that has the specified ID.

Request

To test a cloud failover plan, send the POST HTTP request to the /cloud/cloudFailoverPlans/{ID}?action=test URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}?action=test |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

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

In the response body, the REST API returns a task. Additionally, the REST API returns a URL to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL.

The task is created to start a cloud failover session. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task with the Finished state contains a link to an entity representation of the cloud failover session. To track the session state, send the [GET /cloud/failoverSessions/{ID}](get_cloudfailoversessions_id.md) request.

Example

The example below tests a cloud failover plan that has ID 3f56fa52-c902-4655-9774-2022fde214d2.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2022fde214d2?action=test    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

To track the state of the received task, send the GET HTTP request to the task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Href="https://localhost:9398/api/cloud/failoverSessions/a986d473-0248-4884-9832-17ec982ee393?format=Entity" Name="ABC Company Failover Plan" Type="CloudFailoverSession"/>    </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartCloudFailoverPlan</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

To track the testing progress, send the GET HTTP request to the received cloud failover session:

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/failoverSessions/a986d473-0248-4884-9832-17ec982ee393?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudFailoverSession xmlns="http://www.veeam.com/ent/v1.0" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/a986d473-0248-4884-9832-17ec982ee393?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:a986d473-0248-4884-9832-17ec982ee393">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/4ceb4e03-d23d-4c4e-be05-21580b260243" Name="srv13.tech.local" />     <Link Rel="Alternate" Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/a986d473-0248-4884-9832-17ec982ee393" Name="ABC Company Failover Plan" />   </Links>   <JobType>FailoverPlan</JobType>   <CreationTimeUTC>2020-05-06T20:29:45.077Z</CreationTimeUTC>   <State>Working</State>   <Result>None</Result>   <Progress>0</Progress>   <CloudFailoverTasks>     <CloudFailoverTasks VmName="filesrv03">       <VmReplicaPointLink Rel="Related" Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/c1beab6b-2b18-47f1-9e71-354ab8a49fc2" Name="filesrv03@2020-02-13 05:00:46" />       <CreationTimeUTC>2020-05-06T20:29:50.13Z</CreationTimeUTC>       <State>Working</State>       <Result>None</Result>       <Progress>0</Progress>     </CloudFailoverTasks>     <CloudFailoverTasks VmName="filesrv04">       <VmReplicaPointLink Rel="Related" Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/796cbc20-c2be-4acf-bc1a-4e1e32d7df46" Name="filesrv04@2020-02-13 06:02:20" />       <CreationTimeUTC>2020-05-06T20:29:50.14Z</CreationTimeUTC>       <State>Starting</State>       <Result>None</Result>       <Progress>0</Progress>     </CloudFailoverTasks>   </CloudFailoverTasks> </CloudFailoverSession> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
