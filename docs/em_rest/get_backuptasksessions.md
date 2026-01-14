---
title: "get_backuptasksessions"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backuptasksessions.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of backup task sessions that are performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup task sessions, send the [GET /query?type=BackupTaskSession](get_query_backuptasksession.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V
* Veeam Agent computers running Microsoft Windows or Linux

Request

To get a list of backup task sessions, send the GET HTTP request to the /backupTaskSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupTaskSessions |

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

In the response body, the REST API returns a representation of the /backupTaskSessions resource collection.

Example

The example below returns a list of all backup tasks performed on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupTaskSessions    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body: |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
