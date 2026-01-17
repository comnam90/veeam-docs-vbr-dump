---
title: "GET /query?type=Task"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_task.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=Task


Returns a resource representation of a collection of tasks created by Veeam Backup Enterprise Manager within the currently existing logon session. For details, see [/tasks](tasks.md).

Request

To get a list of tasks, send the GET HTTP request to the query with the type parameter set to Task.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=Task |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| TaskId | String | ID of the task resource, for example: task-1. |
| State | String | State of the task. Possible values:   * Running — the task is in progress. * OperationFinished — the task operation is finished on the backup server, but Veeam Backup Enterprise Manager has not collected the operation data yet. * Finished — the task operation is finished, and the Veeam Backup Enterprise Manager database contains the operation data. |
| Operation | String | Name of the task operation, for example: StartJob. |

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

In the response body, the REST API returns a representation of the /tasks resource collection.

Example

The example below returns a collection of finished tasks created by Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=Task&filter=State==Finished    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


