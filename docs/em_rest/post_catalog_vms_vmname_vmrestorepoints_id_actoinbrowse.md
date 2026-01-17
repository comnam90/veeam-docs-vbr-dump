---
title: "POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_catalog_vms_vmname_vmrestorepoints_id_actoinbrowse.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse


Starts the guest OS file restore process of the VM from the specified restore point. The VM disks are mounted to the backup server and VM guest OS files become available for restore.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To start the VM guest OS restore process, send the POST HTTP request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

The response body also contains a link to the VM file system that allows you to browse for VM guest OS files.

Example

The example below starts the guest OS files restore process for the srv04 VM from the restore point having ID 7caf66d5-f700-442c-9aa9-8867f031377f:

|  |
| --- |
| Request:  POST https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f?action=browse    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |


