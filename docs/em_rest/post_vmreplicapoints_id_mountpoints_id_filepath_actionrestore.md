---
title: "post_vmreplicapoints_id_mountpoints_id_filepath_actionrestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_vmreplicapoints_id_mountpoints_id_filepath_actionrestore.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Restores a VM replica guest OS file or folder. The file or folder can be restored to its original location on the VM or can be downloaded to the local machine.

For file-level restore to the original location, you can use restore points created by a replication job with enabled guest processing settings. In this case, file-level restore will be performed using the guest OS credentials that are specified in the replication job settings.

Alternatively, if guest processing settings are not enabled for the job, you can specify the guest OS credentials in the body of the request. For details, see [File-Level Restore Options](#tooriginal).

Request

To restore a VM guest OS file or folder, send the POST HTTP request to the /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=restore URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=restore |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the restore process. The body of the request must conform to the  [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain either of the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| ToOriginalLocation | FileRestoreToOriginalSpecInfoType | Use this element if you want to restore the file to the original location. For details, see [File-Level Restore Options](#tooriginal). | No | — |
| ForDirectDownload | — | Use this element if you want to download the restored file. | No | — |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "ForDirectDownload": {}  } |

File-Level Restore Options

You can define the following options for file-level restore to the original location:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Overwrite | Boolean | Defines if the file or folder restored from the backup should overwrite the original file or folder. Possible values:   * True — the file from VM backup (being restored) should replace the file on target. * False — both files should be kept on target.   The default value is False. | Yes | 0/1 |
| PermissionsOnly | Boolean | Defines whether to restore only permissions of the file or folder. The file or folder must exist on the target machine. The feature is supported for Windows machines only.  Possible values:   * True * False   The default value is False. | Yes | 0/1 |
| GuestCredentials | PlainCredentialsType | Guest OS credentials for starting the file-level restore process. For details, see [Guest OS Credentials Options](#guest). | Yes | 0/1 |

Options for file-level restore to the original location are provided in the following format:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <FileRestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <ToOriginalLocation Overwrite="false">     <GuestCredentials>       <UserName>fileserver01\administrator</UserName>       <Password>P@ssw0rd</Password>     </GuestCredentials>   </ToOriginalLocation> </FileRestoreSpec> |

JSON Representation

|  |
| --- |
| {   "ToOriginalLocation": {     "GuestCredentials": {       "UserName": "fileserver01\\administrator",       "Password": "P@ssw0rd"     },     "Overwrite": false   }  } |

Guest Credentials Options

You must define the following parameters for the guest OS credentials:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Username | String | User name of the guest OS account specified in the DOMAIN\USENAME format. | Yes | 1/1 |
| Password | String | Password for the guest OS account. | Yes | 1/1 |

Guest OS credentials for starting the file-level restore process are provided in the following format:

XML Representation

|  |
| --- |
| <GuestCredentials>   <UserName>fileserver01\administrator</UserName>   <Password>P@ssw0rd</Password> </GuestCredentials> |

JSON Representation

|  |
| --- |
| "GuestCredentials": {   "UserName": "fileserver01\\administrator",   "Password": "P@ssw0rd"  } |

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

|  |
| --- |
| Note |
| If you have selected to download a restored file or folder, the response body of the task resource will also contain links to files that can be downloaded and saved. |

Example

The example below lets the client restore the C:\Documentation 2014\Invoices\bank\_details.txt file from the VM guest OS and download it after restore:

|  |
| --- |
| Request:  POST https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202014/Invoices/bank\_details.txt?action=restore    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <FileRestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <ForDirectDownload/> </FileRestoreSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>FileRestoreFromMountPoint</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Download" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/e:/documentation%202014/invoices/bank\_details.txt?action=download" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>FileRestoreFromMountPoint</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

To download the restored file, find the necessary link component in the resource representation of the task and send the GET HTTP request to the https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=download URL. The file will be downloaded to the default downloads folder on the backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/e:/documentation%202014/invoices/bank\_details.txt?action=download    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  None |

|  |
| --- |
| Note |
| If you work with Veeam Backup Enterprise Manager REST API using a web application as a client (for example, Veeam Backup Enterprise Manager Web Client), a web browser may propose to select whether to open the file, download it to the default downloads folder or download it to the specified folder. |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
